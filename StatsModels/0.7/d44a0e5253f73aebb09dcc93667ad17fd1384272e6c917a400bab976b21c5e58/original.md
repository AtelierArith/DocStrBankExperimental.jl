```
lrtest(mods::StatisticalModel...; atol::Real=0.0)
```

For each sequential pair of statistical models in `mods...`, perform a likelihood ratio test to determine if the first one fits significantly better than the next.

A table is returned containing degrees of freedom (DOF), difference in DOF from the preceding model, log-likelihood, deviance, chi-squared statistic (i.e. absolute value of twice the difference in log-likelihood) and p-value for the comparison between the two models.

Optional keyword argument `atol` controls the numerical tolerance when testing whether the models are nested.

# Examples

Suppose we want to compare the effects of two or more treatments on some result. Our null hypothesis is that `Result ~ 1` fits the data as well as `Result ~ 1 + Treatment`.

```jldoctest
julia> using DataFrames, GLM

julia> dat = DataFrame(Result=[1, 0, 1, 1, 1, 0, 0, 0, 1, 0, 1, 1],
                       Treatment=[1, 1, 1, 2, 2, 2, 1, 1, 1, 2, 2, 2],
                       Other=string.([1, 1, 2, 1, 2, 1, 3, 1, 1, 2, 2, 1]));

julia> nullmodel = glm(@formula(Result ~ 1), dat, Binomial(), LogitLink());

julia> model = glm(@formula(Result ~ 1 + Treatment), dat, Binomial(), LogitLink());

julia> bigmodel = glm(@formula(Result ~ 1 + Treatment + Other), dat, Binomial(), LogitLink());

julia> lrtest(nullmodel, model, bigmodel)
Likelihood-ratio test: 3 models fitted on 12 observations
────────────────────────────────────────────────────
     DOF  ΔDOF   LogLik  Deviance   Chisq  p(>Chisq)
────────────────────────────────────────────────────
[1]    1        -8.1503   16.3006
[2]    2     1  -7.9780   15.9559  0.3447     0.5571
[3]    4     2  -7.0286   14.0571  1.8988     0.3870
────────────────────────────────────────────────────

julia> lrtest(bigmodel, model, nullmodel)
Likelihood-ratio test: 3 models fitted on 12 observations
────────────────────────────────────────────────────
     DOF  ΔDOF   LogLik  Deviance   Chisq  p(>Chisq)
────────────────────────────────────────────────────
[1]    4        -7.0286   14.0571
[2]    2    -2  -7.9780   15.9559  1.8988     0.3870
[3]    1    -1  -8.1503   16.3006  0.3447     0.5571
────────────────────────────────────────────────────
```
