```
ftest(mod::LinearModel)
```

Perform an F-test to determine whether model `mod` fits significantly better than the null model (i.e. which includes only the intercept).

```jldoctest; setup = :(using DataFrames, GLM)
julia> dat = DataFrame(Result=[1.1, 1.2, 1, 2.2, 1.9, 2, 0.9, 1, 1, 2.2, 2, 2],
                       Treatment=[1, 1, 1, 2, 2, 2, 1, 1, 1, 2, 2, 2]);


julia> model = lm(@formula(Result ~ 1 + Treatment), dat);


julia> ftest(model.model)
F-test against the null model:
F-statistic: 241.62 on 12 observations and 1 degrees of freedom, p-value: <1e-07
```
