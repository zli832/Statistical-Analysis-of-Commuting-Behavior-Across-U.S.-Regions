## Effect of Education, Income, and Geography on Commuting Behaviors

•⁠ Project: Data pipeline& Dashboard + Statistical Model with Python
•⁠ Duration: Feb 2025 - May 2025
•⁠ Team Members: Lucas Li, Reese Yang, Max Migdon

***💻Background***

This project investigates how socioeconomic factors—specifically education level, income, and geographical characteristics—influence commuting behaviors in the United States. Using microdata from the IPUMS American Community Survey (ACS), this analysis explores patterns in commute time, travel mode, and work hours across demographic groups.

The goal is to understand the determinants of commuting burden and mobility behavior, which are relevant for urban planning, labor economics, and public policy.

***📊 Project Overview***

Commuting is a daily necessity that is often shaped by education, income, and social status, all of which can influence transportation choices and travel time. Higher-income and well-educated individuals typically have more flexibility in selecting housing and commuting modes, whereas lower-income workers often face longer, less efficient commutes due to affordability constraints. 

We aim to gain a deeper understanding of these disparities, as this knowledge is essential for policymakers and urban planners seeking to enhance transit equity and economic mobility. In addition, we hope to explore how these socioeconomic factors shape commuting behaviors and have a broader impact on urban accessibility, as well as how certain commuting behaviors, such as vehicles bought and carpooling, relate to the sustainability efforts of each individual.

The project uses large-scale U.S. microdata to identify statistical patterns and build interpretable models.


***Exploratory Data Analysis***
1. Income Distribution: The income distribution exhibits a bimodal pattern with concentration in two primary ranges. 
2. Education Distribution: Education attainment shows a right-skewed distribution with high frequency at lower education levels. 
3. Transit Time Distribution: Transit times follow a multimodal distribution with peak concentrations at 25-30 units and 35-40 units. 
4. Population Density: Population density shows an exponential decay pattern with exceptionally high concentration in low-density areas.
5. Vehicles per Household: Vehicle ownership displays a unimodal distribution peaking at 2 vehicles per household.
6. Carpool Status: The carpool adoption rate shows 88.8% of observations fall in the non-carpool category while only 11.2% represent carpool arrangements, indicating carpooling remains a minority transportation in the US.

We computed the Pearson correlation matrix for six selected variables related to household characteristics and transportation and visualized the correlations using a heatmap.

The heatmap reveals a positive correlation between vehicle ownership and both household income and commuting time, suggesting that higher-income households and those with longer commutes tend to own more vehicles. Conversely, vehicle ownership is negatively correlated with education level and population density, suggesting that individuals with higher education or those residing in denser areas may rely less on personal vehicles.

We categorized the Region variable into four groups: Northeast, Midwest, South, and West. Histogram analysis suggests that individuals in the South and West are more likely to carpool, while those in the Northeast and South tend to have longer commute times. These patterns are consistent with observed differences in population density across regions. However, due to multicollinearity concerns, we excluded DENSITY from the regression models to avoid distortion in coefficient estimates.

Multicollinearity diagnostics show that most Variance Inflation Factors (VIFs) are below the standard threshold of 10, though log(HHINCOME) and SEX show moderately elevated VIFs, indicating some collinearity but not enough to undermine the model.

Conclusion: Household income, regional location, and commuting patterns are significant predictors of vehicle ownership, while carpooling shows no robust effect.

***Result***
In Model 1, we include the logarithm of household income and a binary variable for sex. The coefficient on log(HHINCOME) is 0.467 (p < 0.01), indicating that a 1% increase in household income is associated with an approximate 0.00467 increase in vehicle ownership. The coefficient on SEX is negative and significant at the 1% level (-0.064), suggesting that households with female respondents tend to own fewer vehicles, holding income constant.

Model 2 extends the specification by including region fixed effects (Northeast, South, West, with Midwest as the omitted category). Regional variation is statistically significant: compared to the Midwest, households in the Northeast and South own fewer vehicles (coefficients: -0.231 and -0.047, respectively), while households in the West own slightly more (+0.026). All coefficients are statistically significant at the 1% level.

In Model 3, we control for commute time (TRANTIME). The coefficient on TRANTIME is small but positive and statistically significant (0.0006, p < 0.01), implying that households with longer average commute times are marginally more likely to own additional vehicles, all else equal.

Model 4 includes all prior variables plus a carpooling indicator (CARPOOL). The coefficient on CARPOOL is negative (-0.0046) but not statistically significant (p = 0.145), suggesting that after controlling for income, region, and commute time, carpooling behavior is not a significant predictor of the number of household vehicles.

The R-squared values increase across models: from 0.103 in Model 1 to 0.133 in Model 4, reflecting improved model fit as more covariates are introduced.

A joint F-test on all explanatory variables in Model 4 yields an F-statistic of 21,013.44 (p < 0.0001), well above the critical value at the 1% level (2.639), allowing us to reject the null hypothesis that the coefficients are jointly insignificant.

To check for multicollinearity, we compute Variance Inflation Factors (VIFs). Most variables fall well below the conventional threshold of 10, though log(HHINCOME) and SEX have moderately elevated VIFs of 14.19 and 9.22, respectively. While this may indicate some collinearity, it does not appear to distort the model substantially.

Overall, the results suggest that household income, regional location, and commuting behavior are significant predictors of vehicle ownership.

***Literature Review***

Source 1: https://journals.sagepub.com/doi/10.1177/03611981241233285?icid=int.sj-abstract.citing-articles.1、
Source 2: https://link.springer.com/article/10.1007/s11116-020-10124-w
Source 3: https://www.economist.com/1843/2016/11/28/rethinking-the-commute
Source 4: https://graphics.wsj.com/urban-income-polarization/
Source 5: https://www.economist.com/graphic-detail/2017/01/31/how-colleges-affect-social-mobility-in-america

Education, income, and social status play significant roles in shaping commuting behaviors, influencing both the mode of transportation and the duration of commutes. Higher levels of education are often associated with greater job opportunities, which can lead to longer commutes as individuals seek employment in high-paying urban centers (Sage Journals, Springer). Income levels, on the other hand, affect commuting flexibility—wealthier individuals have greater access to private vehicles or premium public transit options, while lower-income workers may face longer, less efficient commutes due to reliance on public transportation and carpooling (WSJ, Economist). Social status and neighborhood income distribution further impact commuting efficiency, with wealthier areas having better infrastructure and transportation networks, whereas lower-income regions often experience inadequate transit options, reinforcing economic disparities (Economist, WSJ). Ultimately, these factors create a commuting landscape where privilege affords convenience, while socioeconomic constraints can exacerbate commuting burdens.

***📫 Contact***
If you have questions about this project, feel free to reach out:

Lucas Li
📧 zhengxiang210207@gmail.com
