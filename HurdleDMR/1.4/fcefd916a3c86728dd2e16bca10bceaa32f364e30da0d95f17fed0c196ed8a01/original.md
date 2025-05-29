```
fit(::CIR{BM,FM},covars,counts,projdir[,fmargs...]; <keyword arguments>)
```

Fit a Counts Inverse Regression (CIR) of `covars[:,projdir] ~ counts + covars[:,~projdir]`.

CIR involves three steps:

1. Fit a backward regression model BM<:DCR: counts ~ covars
2. Calculate an sufficient reduction projection in direction projdir
3. Fit a forward regression model FM<:RegressionModel:

```
covars[:,projdir] ~ srproj(counts) + covars[:,~projdir]
```

# Example:

```julia
  m = fit(CIR{DMR,LinearModel}, covars, counts, 1; nocounts=true)
  yhat = predict(m, covars, counts)
  yhatnc = predict(m, covars, counts; nocounts=true)
```

# Arguments

  * `covars` n-by-p matrix of covariates
  * `counts` n-by-d matrix of counts (usually sparse)
  * `projdir` index of covars column used as dependent variable in forward model
  * `fmargs...` optional arguments passed along to the forward regression model

# Keywords

  * `nocounts::Bool=false` whether to also fit a benchmark model without counts
  * `bmkwargs...` keyword arguments passed along to the backward regression model
