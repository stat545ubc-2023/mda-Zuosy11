Mini Data-Analysis Deliverable 1
================

# Welcome to your (maybe) first-ever data analysis project!

And hopefully the first of many. Let’s get started:

1.  Install the [`datateachr`](https://github.com/UBC-MDS/datateachr)
    package by typing the following into your **R terminal**:

<!-- -->

    install.packages("devtools")
    devtools::install_github("UBC-MDS/datateachr")

2.  Load the packages below.

``` r
library(datateachr)
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.3     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

3.  Make a repository in the <https://github.com/stat545ubc-2023>
    Organization. You can do this by following the steps found on canvas
    in the entry called [MDA: Create a
    repository](https://canvas.ubc.ca/courses/126199/pages/mda-create-a-repository).
    One completed, your repository should automatically be listed as
    part of the stat545ubc-2023 Organization.

# Instructions

## For Both Milestones

- Each milestone has explicit tasks. Tasks that are more challenging
  will often be allocated more points.

- Each milestone will be also graded for reproducibility, cleanliness,
  and coherence of the overall Github submission.

- While the two milestones will be submitted as independent
  deliverables, the analysis itself is a continuum - think of it as two
  chapters to a story. Each chapter, or in this case, portion of your
  analysis, should be easily followed through by someone unfamiliar with
  the content.
  [Here](https://swcarpentry.github.io/r-novice-inflammation/06-best-practices-R/)
  is a good resource for what constitutes “good code”. Learning good
  coding practices early in your career will save you hassle later on!

- The milestones will be equally weighted.

## For Milestone 1

**To complete this milestone**, edit [this very `.Rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-1.Rmd)
directly. Fill in the sections that are tagged with
`<!--- start your work below --->`.

**To submit this milestone**, make sure to knit this `.Rmd` file to an
`.md` file by changing the YAML output settings from
`output: html_document` to `output: github_document`. Commit and push
all of your work to the mini-analysis GitHub repository you made
earlier, and tag a release on GitHub. Then, submit a link to your tagged
release on canvas.

**Points**: This milestone is worth 36 points: 30 for your analysis, and
6 for overall reproducibility, cleanliness, and coherence of the Github
submission.

# Learning Objectives

By the end of this milestone, you should:

- Become familiar with your dataset of choosing
- Select 4 questions that you would like to answer with your data
- Generate a reproducible and clear report using R Markdown
- Become familiar with manipulating and summarizing your data in tibbles
  using `dplyr`, with a research question in mind.

# Task 1: Choose your favorite dataset

The `datateachr` package by Hayley Boyce and Jordan Bourak currently
composed of 7 semi-tidy datasets for educational purposes. Here is a
brief description of each dataset:

- *apt_buildings*: Acquired courtesy of The City of Toronto’s Open Data
  Portal. It currently has 3455 rows and 37 columns.

- *building_permits*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 20680 rows and 14 columns.

- *cancer_sample*: Acquired courtesy of UCI Machine Learning Repository.
  It currently has 569 rows and 32 columns.

- *flow_sample*: Acquired courtesy of The Government of Canada’s
  Historical Hydrometric Database. It currently has 218 rows and 7
  columns.

- *parking_meters*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 10032 rows and 22 columns.

- *steam_games*: Acquired courtesy of Kaggle. It currently has 40833
  rows and 21 columns.

- *vancouver_trees*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 146611 rows and 20 columns.

**Things to keep in mind**

- We hope that this project will serve as practice for carrying our your
  own *independent* data analysis. Remember to comment your code, be
  explicit about what you are doing, and write notes in this markdown
  document when you feel that context is required. As you advance in the
  project, prompts and hints to do this will be diminished - it’ll be up
  to you!

- Before choosing a dataset, you should always keep in mind **your
  goal**, or in other ways, *what you wish to achieve with this data*.
  This mini data-analysis project focuses on *data wrangling*,
  *tidying*, and *visualization*. In short, it’s a way for you to get
  your feet wet with exploring data on your own.

And that is exactly the first thing that you will do!

1.1 **(1 point)** Out of the 7 datasets available in the `datateachr`
package, choose **4** that appeal to you based on their description.
Write your choices below:

**Note**: We encourage you to use the ones in the `datateachr` package,
but if you have a dataset that you’d really like to use, you can include
it here. But, please check with a member of the teaching team to see
whether the dataset is of appropriate complexity. Also, include a
**brief** description of the dataset here to help the teaching team
understand your data.

<!-------------------------- Start your work below ---------------------------->

1: *steam_games*  
2: *parking_meters*  
3: *building_permits*  
4: *apt_buildings*

<!----------------------------------------------------------------------------->

1.2 **(6 points)** One way to narrowing down your selection is to
*explore* the datasets. Use your knowledge of dplyr to find out at least
*3* attributes about each of these datasets (an attribute is something
such as number of rows, variables, class type…). The goal here is to
have an idea of *what the data looks like*.

*Hint:* This is one of those times when you should think about the
cleanliness of your analysis. I added a single code chunk for you below,
but do you want to use more than one? Would you like to write more
comments outside of the code chunk?

<!-------------------------- Start your work below ---------------------------->

The three attributes are chosen to be 1) the number of rows and 2)
columns/variables, and 3) the class type. I will use head(), nrow(), and
class() to explore the selected datasets.

1)  steam_games:

``` r
head(steam_games)
```

    ## # A tibble: 6 × 21
    ##      id url     types name  desc_snippet recent_reviews all_reviews release_date
    ##   <dbl> <chr>   <chr> <chr> <chr>        <chr>          <chr>       <chr>       
    ## 1     1 https:… app   DOOM  Now include… Very Positive… Very Posit… May 12, 2016
    ## 2     2 https:… app   PLAY… PLAYERUNKNO… Mixed,(6,214)… Mixed,(836… Dec 21, 2017
    ## 3     3 https:… app   BATT… Take comman… Mixed,(166),-… Mostly Pos… Apr 24, 2018
    ## 4     4 https:… app   DayZ  The post-so… Mixed,(932),-… Mixed,(167… Dec 13, 2018
    ## 5     5 https:… app   EVE … EVE Online … Mixed,(287),-… Mostly Pos… May 6, 2003 
    ## 6     6 https:… bund… Gran… Grand Theft… NaN            NaN         NaN         
    ## # ℹ 13 more variables: developer <chr>, publisher <chr>, popular_tags <chr>,
    ## #   game_details <chr>, languages <chr>, achievements <dbl>, genre <chr>,
    ## #   game_description <chr>, mature_content <chr>, minimum_requirements <chr>,
    ## #   recommended_requirements <chr>, original_price <dbl>, discount_price <dbl>

steam_games has 21 columns/variables. Most of them are of completely
character type, while the remaining ones are of double type. In my view,
extracting information from character variables, especially when they
are the most important, could prove to be quite challenging.

The class type and number of rows of steam_games:

``` r
class(steam_games)
```

    ## [1] "spec_tbl_df" "tbl_df"      "tbl"         "data.frame"

``` r
nrow(steam_games)
```

    ## [1] 40833

In conclusion, steam_games is a 40833x21 tibble with many \<chr\>
variables.

2)  parking_meters

``` r
head(parking_meters)
```

    ## # A tibble: 6 × 22
    ##   meter_head  r_mf_9a_6p r_mf_6p_10 r_sa_9a_6p r_sa_6p_10 r_su_9a_6p r_su_6p_10
    ##   <chr>       <chr>      <chr>      <chr>      <chr>      <chr>      <chr>     
    ## 1 Twin        $2.00      $4.00      $2.00      $4.00      $2.00      $4.00     
    ## 2 Pay Station $1.00      $1.00      $1.00      $1.00      $1.00      $1.00     
    ## 3 Twin        $1.00      $1.00      $1.00      $1.00      $1.00      $1.00     
    ## 4 Single      $1.00      $1.00      $1.00      $1.00      $1.00      $1.00     
    ## 5 Twin        $2.00      $1.00      $2.00      $1.00      $2.00      $1.00     
    ## 6 Twin        $2.00      $1.00      $2.00      $1.00      $2.00      $1.00     
    ## # ℹ 15 more variables: rate_misc <chr>, time_in_effect <chr>, t_mf_9a_6p <chr>,
    ## #   t_mf_6p_10 <chr>, t_sa_9a_6p <chr>, t_sa_6p_10 <chr>, t_su_9a_6p <chr>,
    ## #   t_su_6p_10 <chr>, time_misc <chr>, credit_card <chr>, pay_phone <chr>,
    ## #   longitude <dbl>, latitude <dbl>, geo_local_area <chr>, meter_id <chr>

parking_meters has 22 columns/variables. Although most of them are also
\<chr\>, they are just numbers with a unit or symbol such as Hr or \$,
which is easy to extract.

The class type and number of rows of parking_meters:

``` r
class(parking_meters)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
nrow(parking_meters)
```

    ## [1] 10032

In conclusion, parking_meters is a 10032x22 tibble with simpler and
clearer variables.

3)  building_permits

``` r
head(building_permits)
```

    ## # A tibble: 6 × 14
    ##   permit_number issue_date project_value type_of_work          address          
    ##   <chr>         <date>             <dbl> <chr>                 <chr>            
    ## 1 BP-2016-02248 2017-02-01             0 Salvage and Abatement 4378 W 9TH AVENU…
    ## 2 BU468090      2017-02-01             0 New Building          1111 RICHARDS ST…
    ## 3 DB-2016-04450 2017-02-01         35000 Addition / Alteration 3732 W 12TH AVEN…
    ## 4 DB-2017-00131 2017-02-01         15000 Addition / Alteration 88 W PENDER STRE…
    ## 5 DB452250      2017-02-01        181178 New Building          492 E 62ND AVENU…
    ## 6 BP-2016-01458 2017-02-02             0 Salvage and Abatement 3332 W 28TH AVEN…
    ## # ℹ 9 more variables: project_description <chr>, building_contractor <chr>,
    ## #   building_contractor_address <chr>, applicant <chr>,
    ## #   applicant_address <chr>, property_use <chr>, specific_use_category <chr>,
    ## #   year <dbl>, bi_id <dbl>

building_permits comprises 14 columns/variables, which is comparatively
fewer than the two datasets mentioned earlier. Nonetheless, it not only
includes numerous \<chr\> variables but also contains a significant
number of missing (NA) values, making it challenging for analysis and
manipulation.

The class type and number of rows of building_permits:

``` r
class(building_permits)
```

    ## [1] "spec_tbl_df" "tbl_df"      "tbl"         "data.frame"

``` r
nrow(building_permits)
```

    ## [1] 20680

In conclusion, building_permits is a 20680x14 tibble with many \<chr\>
variables and missing values.

4)  apt_buildings

``` r
head(apt_buildings)
```

    ## # A tibble: 6 × 37
    ##      id air_conditioning amenities balconies barrier_free_accessi…¹ bike_parking
    ##   <dbl> <chr>            <chr>     <chr>     <chr>                  <chr>       
    ## 1 10359 NONE             Outdoor … YES       YES                    0 indoor pa…
    ## 2 10360 NONE             Outdoor … YES       NO                     0 indoor pa…
    ## 3 10361 NONE             <NA>      YES       NO                     Not Availab…
    ## 4 10362 NONE             <NA>      YES       YES                    Not Availab…
    ## 5 10363 NONE             <NA>      NO        NO                     12 indoor p…
    ## 6 10364 NONE             <NA>      NO        NO                     Not Availab…
    ## # ℹ abbreviated name: ¹​barrier_free_accessibilty_entr
    ## # ℹ 31 more variables: exterior_fire_escape <chr>, fire_alarm <chr>,
    ## #   garbage_chutes <chr>, heating_type <chr>, intercom <chr>,
    ## #   laundry_room <chr>, locker_or_storage_room <chr>, no_of_elevators <dbl>,
    ## #   parking_type <chr>, pets_allowed <chr>, prop_management_company_name <chr>,
    ## #   property_type <chr>, rsn <dbl>, separate_gas_meters <chr>,
    ## #   separate_hydro_meters <chr>, separate_water_meters <chr>, …

apt_buildings consists of 37 columns/variables, which is considerably
more than the previously mentioned datasets. However, it’s important to
note that the majority of these columns only contain binary logical
values, typically represented as “YES” or “NO.” While having a large
number of columns can make the dataset more comprehensive, the dominance
of binary values simplifies the nature of the data, potentially making
it easier to work with for specific analytical tasks that involve
Boolean conditions or criteria.

The class type and number of rows of building_permits:

``` r
class(apt_buildings)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

``` r
nrow(apt_buildings)
```

    ## [1] 3455

In conclusion, apt_buildings is a 3455x37 tibble. It doesn’t have many
rows and the columns are predominantly logical values.

<!----------------------------------------------------------------------------->

1.3 **(1 point)** Now that you’ve explored the 4 datasets that you were
initially most interested in, let’s narrow it down to 1. What lead you
to choose this one? Briefly explain your choice below.

<!-------------------------- Start your work below ---------------------------->

I would choose parking_meters to be my preference.

First, it has a moderate number of rows and columns, suggesting that it
is neither too small nor excessively large for conducting analysis.

Second, it contains simple but straightforward variables, including time
intervals or coordinates, which could be meaningful and interesting to
visualize.

Third, it doesn’t contain many missing values. Having relatively few
missing values simplifies data cleaning and imputation, making it more
suitable for analysis.

<!----------------------------------------------------------------------------->

1.4 **(2 points)** Time for a final decision! Going back to the
beginning, it’s important to have an *end goal* in mind. For example, if
I had chosen the `titanic` dataset for my project, I might’ve wanted to
explore the relationship between survival and other variables. Try to
think of 1 research question that you would want to answer with your
dataset. Note it down below.

<!-------------------------- Start your work below ---------------------------->

What is the relationship between the parking meters’ rates and their
geographical location?

<!----------------------------------------------------------------------------->

# Important note

Read Tasks 2 and 3 *fully* before starting to complete either of them.
Probably also a good point to grab a coffee to get ready for the fun
part!

This project is semi-guided, but meant to be *independent*. For this
reason, you will complete tasks 2 and 3 below (under the **START HERE**
mark) as if you were writing your own exploratory data analysis report,
and this guidance never existed! Feel free to add a brief introduction
section to your project, format the document with markdown syntax as you
deem appropriate, and structure the analysis as you deem appropriate. If
you feel lost, you can find a sample data analysis
[here](https://www.kaggle.com/headsortails/tidy-titarnic) to have a
better idea. However, bear in mind that it is **just an example** and
you will not be required to have that level of complexity in your
project.

# Task 2: Exploring your dataset

If we rewind and go back to the learning objectives, you’ll see that by
the end of this deliverable, you should have formulated *4* research
questions about your data that you may want to answer during your
project. However, it may be handy to do some more exploration on your
dataset of choice before creating these questions - by looking at the
data, you may get more ideas. **Before you start this task, read all
instructions carefully until you reach START HERE under Task 3**.

2.1 **(12 points)** Complete *4 out of the following 8 exercises* to
dive deeper into your data. All datasets are different and therefore,
not all of these tasks may make sense for your data - which is why you
should only answer *4*.

Make sure that you’re using dplyr and ggplot2 rather than base R for
this task. Outside of this project, you may find that you prefer using
base R functions for certain tasks, and that’s just fine! But part of
this project is for you to practice the tools we learned in class, which
is dplyr and ggplot2.

1.  Plot the distribution of a numeric variable.
2.  Create a new variable based on other variables in your data (only if
    it makes sense)
3.  Investigate how many missing values there are per variable. Can you
    find a way to plot this?
4.  Explore the relationship between 2 variables in a plot.
5.  Filter observations in your data according to your own criteria.
    Think of what you’d like to explore - again, if this was the
    `titanic` dataset, I may want to narrow my search down to passengers
    born in a particular year…
6.  Use a boxplot to look at the frequency of different observations
    within a single variable. You can do this for more than one variable
    if you wish!
7.  Make a new tibble with a subset of your data, with variables and
    observations that you are interested in exploring.
8.  Use a density plot to explore any of your variables (that are
    suitable for this type of plot).

2.2 **(4 points)** For each of the 4 exercises that you complete,
provide a *brief explanation* of why you chose that exercise in relation
to your data (in other words, why does it make sense to do that?), and
sufficient comments for a reader to understand your reasoning and code.

<!-------------------------- Start your work below ---------------------------->

I chose Ex.3, 4, 6, and 7.

Ex.3: It is important to notice how many missing values are in the
dataset. Too many missing values will severely affect the accuracy of
the relationships conducted. By this exercise I’ve found that rate_misc
and time_misc contain too many missing values and should be discarded.

Ex.4: I’ve visualized the relationship between parking rates on
Saturdays from 9 AM to 6 PM and geo local areas, which has provided a
clear representation of the rate distribution. This serves as a
promising starting point for extending the analysis to encompass all
time slots throughout the week.

Ex.6: Using boxplots helps me understand how parking rates are spread
out, identify potential outliers, and compare distributions in a simple
way.

Ex.7: I’ve removed irrelevant variables to simplify the tibble for
easier manipulation. In further analysis, I’ll rename the shortened
variable names to make them more understandable.

------------------------------------------------------------------------

Ex.3 Investigate how many missing values there are per variable. Can you
find a way to plot this?

``` r
ex_3 <- parking_meters %>%
  summarise_all(~sum(is.na(.)))
print(ex_3)
```

    ## # A tibble: 1 × 22
    ##   meter_head r_mf_9a_6p r_mf_6p_10 r_sa_9a_6p r_sa_6p_10 r_su_9a_6p r_su_6p_10
    ##        <int>      <int>      <int>      <int>      <int>      <int>      <int>
    ## 1          0         20         20         23         20         23         20
    ## # ℹ 15 more variables: rate_misc <int>, time_in_effect <int>, t_mf_9a_6p <int>,
    ## #   t_mf_6p_10 <int>, t_sa_9a_6p <int>, t_sa_6p_10 <int>, t_su_9a_6p <int>,
    ## #   t_su_6p_10 <int>, time_misc <int>, credit_card <int>, pay_phone <int>,
    ## #   longitude <int>, latitude <int>, geo_local_area <int>, meter_id <int>

At first glance, it’s evident that the ‘rate_misc’ and ‘time_misc’
variables have significantly more missing values compared to the others.
Consequently, I have decided to exclude them from further analysis. We
can proceed to visualize the remaining variables:

``` r
ex_3.1 <- ex_3 %>%
  select(-c(rate_misc, time_misc)) %>%
  pivot_longer(everything(), names_to = "var", values_to = "count") %>%
  ggplot(aes(var,count)) + 
  labs(title = "Missing Value of Each Variable") +
  geom_col(fill = 'lightblue') +
  theme(axis.text.x = element_text(size = 4))
print(ex_3.1)
```

![](mm_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

Ex.4 Explore the relationship between 2 variables in a plot.

``` r
ex_4 <- ggplot(parking_meters) + 
  geom_bar(aes(x = r_sa_9a_6p, fill = geo_local_area)) + 
  theme(axis.text.x = element_text(size = 6)) +
  labs(
    title = "Relationship between Saturday 9AM-6PM Parking Rates and Geo Local Area",
    x = "Parking Rate on Sat. 9AM-6PM",
    y = "Count"
  )+
  theme(plot.title = element_text(size = 9))
  
print(ex_4)
```

![](mm_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

Ex.6 Use a boxplot to look at the frequency of different observations
within a single variable. You can do this for more than one variable if
you wish!

``` r
ex_6 <- ggplot(parking_meters,aes(geo_local_area,as.numeric(gsub("\\$","",r_sa_9a_6p)))) +
geom_boxplot(fill = "lightblue",na.rm = TRUE) + 
coord_flip()+
labs(
  title = "Boxplot of Parking Rate on Sat.9AM-6PM by Geo Local Area",
  x = "Geo Local Area",
  y = "Parking Rate on Sat.9AM-6PM") + 
scale_y_continuous(labels = scales::dollar_format())
print(ex_6)
```

![](mm_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

Ex.7 Make a new tibble with a subset of your data, with variables and
observations that you are interested in exploring.

I am only interested in the rates, time limits, credit card acceptance,
coordinates and locations. Therefore I dropped other variables.

``` r
ex_7 <- select(parking_meters, -c(meter_head,rate_misc,time_in_effect,time_misc,pay_phone,meter_id))
print(ex_7)
```

    ## # A tibble: 10,032 × 16
    ##    r_mf_9a_6p r_mf_6p_10 r_sa_9a_6p r_sa_6p_10 r_su_9a_6p r_su_6p_10 t_mf_9a_6p
    ##    <chr>      <chr>      <chr>      <chr>      <chr>      <chr>      <chr>     
    ##  1 $2.00      $4.00      $2.00      $4.00      $2.00      $4.00      2 Hr      
    ##  2 $1.00      $1.00      $1.00      $1.00      $1.00      $1.00      10 Hrs    
    ##  3 $1.00      $1.00      $1.00      $1.00      $1.00      $1.00      2 Hr      
    ##  4 $1.00      $1.00      $1.00      $1.00      $1.00      $1.00      2 Hr      
    ##  5 $2.00      $1.00      $2.00      $1.00      $2.00      $1.00      2 Hr      
    ##  6 $2.00      $1.00      $2.00      $1.00      $2.00      $1.00      3 Hr      
    ##  7 $2.00      $3.00      $2.00      $3.00      $2.00      $3.00      2 Hr      
    ##  8 $2.00      $3.00      $2.00      $3.00      $2.00      $3.00      2 Hr      
    ##  9 $4.00      $1.00      $4.00      $1.00      $4.00      $1.00      2 Hr      
    ## 10 $2.00      $1.00      $2.00      $1.00      $2.00      $1.00      3 Hr      
    ## # ℹ 10,022 more rows
    ## # ℹ 9 more variables: t_mf_6p_10 <chr>, t_sa_9a_6p <chr>, t_sa_6p_10 <chr>,
    ## #   t_su_9a_6p <chr>, t_su_6p_10 <chr>, credit_card <chr>, longitude <dbl>,
    ## #   latitude <dbl>, geo_local_area <chr>

<!----------------------------------------------------------------------------->

# Task 3: Choose research questions

**(4 points)** So far, you have chosen a dataset and gotten familiar
with it through exploring the data. You have also brainstormed one
research question that interested you (Task 1.4). Now it’s time to pick
4 research questions that you would like to explore in Milestone 2!
Write the 4 questions and any additional comments below.

<!--- *****START HERE***** --->

1.  Are there specific regions within the city that have distinct
    patterns of time limits, and how do these patterns affect parking
    rates? I would like to explore the distribution of parking rates and
    time limits in different areas within the city.

2.  Do areas with shorter time limits tend to have lower parking rates,
    and vice versa? I would like to explore the relationship between
    parking rates and time limits.

3.  Does the acceptance of credit card relate to parking rates? I would
    like to explore whether the payment method will affect the rates.

4.  How do the geographical coordinates (latitude and longitude) of
    parking spaces influence pricing and time limits? In addition to
    analyzing regional patterns, I also plan to plot precise maps of
    parking space coordinates, allowing us to visualize their
    distribution and its relation to pricing and time limits.

<!----------------------------->

# Overall reproducibility/Cleanliness/Coherence Checklist

## Coherence (0.5 points)

The document should read sensibly from top to bottom, with no major
continuity errors. An example of a major continuity error is having a
data set listed for Task 3 that is not part of one of the data sets
listed in Task 1.

## Error-free code (3 points)

For full marks, all code in the document should run without error. 1
point deduction if most code runs without error, and 2 points deduction
if more than 50% of the code throws an error.

## Main README (1 point)

There should be a file named `README.md` at the top level of your
repository. Its contents should automatically appear when you visit the
repository on GitHub.

Minimum contents of the README file:

- In a sentence or two, explains what this repository is, so that
  future-you or someone else stumbling on your repository can be
  oriented to the repository.
- In a sentence or two (or more??), briefly explains how to engage with
  the repository. You can assume the person reading knows the material
  from STAT 545A. Basically, if a visitor to your repository wants to
  explore your project, what should they know?

Once you get in the habit of making README files, and seeing more README
files in other projects, you’ll wonder how you ever got by without them!
They are tremendously helpful.

## Output (1 point)

All output is readable, recent and relevant:

- All Rmd files have been `knit`ted to their output md files.
- All knitted md files are viewable without errors on Github. Examples
  of errors: Missing plots, “Sorry about that, but we can’t show files
  that are this big right now” messages, error messages from broken R
  code
- All of these output files are up-to-date – that is, they haven’t
  fallen behind after the source (Rmd) files have been updated.
- There should be no relic output files. For example, if you were
  knitting an Rmd to html, but then changed the output to be only a
  markdown file, then the html file is a relic and should be deleted.

(0.5 point deduction if any of the above criteria are not met. 1 point
deduction if most or all of the above criteria are not met.)

Our recommendation: right before submission, delete all output files,
and re-knit each milestone’s Rmd file, so that everything is up to date
and relevant. Then, after your final commit and push to Github, CHECK on
Github to make sure that everything looks the way you intended!

## Tagged release (0.5 points)

You’ve tagged a release for Milestone 1.

### Attribution

Thanks to Icíar Fernández Boyano for mostly putting this together, and
Vincenzo Coia for launching.
