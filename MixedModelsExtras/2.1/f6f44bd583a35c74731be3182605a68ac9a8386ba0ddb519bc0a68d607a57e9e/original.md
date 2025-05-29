```
r2(model::LinearMixedModel; conditional=false)
r²(model::LinearMixedModel; conditional=false)
```

Coefficient of determination (R-squared).

R² is very non trivial for mixed models for a number of reasons and the measures here are particularly simplistic. For `conditional=true`, the Pearson correlation between the fitted and observed values is simply squared, in line with the relationship between the coefficient of determination and the Pearson correlation for classical OLS models. For `conditional=false`, new predicted values are generated based on only the fixed-effects estimates and the correlation between these predictions and the observed values is again squared.

In both cases, it is important to note that despite the usual naming convention (R² for the coefficient of determination and r for Pearson's correlation coefficient), these quantitaties are not defined in terms of the other. Instead, the correlation is a standardized measure of covariance and the coefficient of determination is measured relative to a null model. (The total sum of squares is in some sense the squared residual error of the null model.) Even generalizations of the coefficient of determination that define this value in terms of the likelihoods of an intercept-only model (i.e. the sample mean) and the likelihood of the fitted model fail to generalize to the mixed-model case: should "intercept-only" mean truly just the fixed effect (i.e. comparing the likelihoods of a classical OLS and a mixed-effects model)? or should it also include an random intercept for each grouping variable? What is the null model in this case, when determining whether each grouping variable contributes to overall fit? There is no single, clear, agreed-upon answer for these questions.  The bottom line is that there are many potential ways to define a coefficient of determination for linear mixed models (and even more for the generalzed case which combines all the problems of R² for GLM and for LMM) and none of them have all the properties of the coefficient of determination for classical OLS regression.

There are more advanced approximations (see e.g. Nakagawa and colleagues' 2013 2017 papers) but the fundamental philosophical issues above remain. In the future, additional approximations may be supported, but this is not a high priority.  Pull requests are welcome.

For more information, see the [GLMM FAQ](https://bbolker.github.io/mixedmodels-misc/glmmFAQ.html#how-do-i-compute-a-coefficient-of-determination-r2-or-an-analogue-for-glmms)
