```
ModelComparison
```

A struct containing the results of model comparison.

# Fields

  * `pointwise::KeyedArray`: A `KeyedArray` of pointwise estimates. See [`PsisLoo`]@ref.

      * `estimates::KeyedArray`: A table containing the results of model comparison, with the following columns –

          * `cv_elpd`: The difference in total leave-one-out cross validation scores between models.
          * `cv_avg`: The difference in average LOO-CV scores between models.
          * `weight`: A set of Akaike-like weights assigned to each model, which can be used in pseudo-Bayesian model averaging.
      * `std_err::NamedTuple`: A named tuple containing the standard error of `cv_elpd`. Note  that these estimators (incorrectly) assume all folds are independent, despite their  substantial overlap, which creates a downward biased estimator. LOO-CV differences are *not* asymptotically normal, so these standard errors cannot be used to  calculate a confidence interval.
      * `gmpd::NamedTuple`: The geometric mean of the predictive distribution. It equals the  geometric mean of the probability assigned to each data point by the model, that is, `exp(cv_avg)`. This measure is only meaningful for classifiers (variables with discrete  outcomes). We can think of it as measuring how often the model was right: A model that always predicts incorrectly will have a GMPD of 0, while a model that always predicts correctly will have a GMPD of 1. However, the GMPD gives a model "Partial points"  between 0 and 1 whenever the model assigns a probability other than 0 or 1 to the  outcome that actually happened.

See also: [`PsisLoo`](@ref)
