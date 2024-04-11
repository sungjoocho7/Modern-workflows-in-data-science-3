# COVID-19 Analysis

## -Using data from the Center for Systems Science and Engineering (CSSE) at Johns Hopkins University-

## Description

The goal of this project is to analyze the trends of COVID-19 cases between January 22, 2022, and March 9, 2023. The analysis focuses on understanding the overall changes in COVID-19 cases and variations across seven different countries (Germany, China, Japan, United Kingdom, US, Brazil, Mexico, during this period. The dataset in this analysis was obtained from the Center for [Systems Science and Engineering (CSSE) at Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19/tree/4360e50239b4eb6b22f3a1759323748f36752177/csse_covid_19_data). The data was downloaded on 10 April 2024.

Original datasets are UID_ISO_FIPS_LookUp_Table.csv and time_series_covid19_confirmed_global.csv, and the merged dataset was used for this analysis. The final dataset contains variables below:

-   **FIPS**: US only. Federal Information Processing Standards code that uniquely identifies counties within the USA.
-   **UID**: Unique Identifier for each row entry.
-   **ISO3**: Officially assigned country code identifiers.
-   **FIPS**: Federal Information Processing Standards code that uniquely identifies counties within the USA.
-   **Admin2**: County name. US only.
-   **Province_State**: Province, state or dependency name.
-   **Country_Region**: Country, region or sovereignty name. The names of locations included on the Website correspond with the official designations used by the U.S. Department of State.
-   **Lat** and **Long**: Dot locations on the dashboard. All points (except for Australia) shown on the map are based on geographic centroids, and are not representative of a specific address, building or any location at a spatial scale finer than a province/state. Australian dots are located at the centroid of the largest city in each state.
-   **Population**: Population data in the country.
-   **time**: Date of data collection for each case record.
-   **case**: The count of COVID-19 cases recorded.


## Organization of the repo

This repository is organized as follows:

-   **/data** - Contains the merged datasets used in the analysis.
-   **/script** - Contains a markdown document used to generate an analytic notebook.
-   **/report** - Contains an analytic notebook (PDF Rmarkdown) that shows all the syntax and the results for the analysis.
-   **/figs** - Contains figures (plot, etc) generated during the analysis.
-   **/documentation** - Contains instructional documents and a README HTML version.


## Analysis steps

1.  Data cleaning process was conducted in R using RStudio server on Amazon Web Services (AWS).
2.  Two original datasets were merged, retaining only a subset of data comprising Germany, China, Japan, United Kingdom, US, Brazil, and Mexico for further analysis using Spark.
3.  Data analysis was performed in Spark, which involved the following steps:
    -   **Descriptive analysis**: Graphs illustrating the change in the number of cases and the change in rate by country were generated.
    -   **Modeling**: A linear regression model was applied to fit the log of the number of cases, with predictors including country, population size, and day since the start of the pandemic.
    

## Overview of findings from the analysis

The two graphs presented below illustrate how the number of cases and rate change over time by seven selected countries. All seven countries exhibit increasing trends in the number of COVID cases over time. Notably, US has experienced particularly rapid increases in the number of cases, while other countries show a more steady trend. Also, The rate of cases is significantly and rapidly increasing over time in the United Kingdom, whereas other countries exhibit a more steady trend. The linear regression model shows that all predictors (country, population, and days) significantly influence the log number of COVID19 cases.

![](figs/plot_change_case.png)
*Figure 1*

![](figs/plot_change_rate.png)
*Figure 2*


## Session info:
```
R version 4.3.1 (2023-06-16)
Platform: x86_64-pc-linux-gnu (64-bit)
Running under: Ubuntu 22.04.2 LTS

Matrix products: default
BLAS:   /usr/lib/x86_64-linux-gnu/openblas-pthread/libblas.so.3 
LAPACK: /usr/lib/x86_64-linux-gnu/openblas-pthread/libopenblasp-r0.3.20.so;  LAPACK version 3.10.0

locale:
 [1] LC_CTYPE=C.UTF-8       LC_NUMERIC=C           LC_TIME=C.UTF-8        LC_COLLATE=C.UTF-8    
 [5] LC_MONETARY=C.UTF-8    LC_MESSAGES=C.UTF-8    LC_PAPER=C.UTF-8       LC_NAME=C             
 [9] LC_ADDRESS=C           LC_TELEPHONE=C         LC_MEASUREMENT=C.UTF-8 LC_IDENTIFICATION=C   

time zone: Etc/UTC
tzcode source: system (glibc)

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

loaded via a namespace (and not attached):
[1] compiler_4.3.1 tools_4.3.1   
Connected to your session in progress, last started 2024-Apr-11 03:36:35 UTC (10 minutes ago)
> sessionInfo()
R version 4.3.1 (2023-06-16)
Platform: x86_64-pc-linux-gnu (64-bit)
Running under: Ubuntu 22.04.2 LTS

Matrix products: default
BLAS:   /usr/lib/x86_64-linux-gnu/openblas-pthread/libblas.so.3 
LAPACK: /usr/lib/x86_64-linux-gnu/openblas-pthread/libopenblasp-r0.3.20.so;  LAPACK version 3.10.0

locale:
 [1] LC_CTYPE=C.UTF-8       LC_NUMERIC=C           LC_TIME=C.UTF-8        LC_COLLATE=C.UTF-8    
 [5] LC_MONETARY=C.UTF-8    LC_MESSAGES=C.UTF-8    LC_PAPER=C.UTF-8       LC_NAME=C             
 [9] LC_ADDRESS=C           LC_TELEPHONE=C         LC_MEASUREMENT=C.UTF-8 LC_IDENTIFICATION=C   

time zone: Etc/UTC
tzcode source: system (glibc)

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base     

loaded via a namespace (and not attached):
[1] compiler_4.3.1 tools_4.3.1  
```

