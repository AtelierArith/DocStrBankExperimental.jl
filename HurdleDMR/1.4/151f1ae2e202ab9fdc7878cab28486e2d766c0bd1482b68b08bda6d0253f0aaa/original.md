```
fit(CIR{DMR,FM},m,df,counts,projdir[,fmargs...]; <keyword arguments>)
```

Version of fit(CIR{DMR,FM}...) that takes a @model() and a dataframe instead of a covars matrix, and a projdir::Symbol specifies the dependent variable. See also fit(CIR...).

# Example:

```julia
  m = fit(CIR{DMR,LinearModel}, @model(c~x1+x2), df, counts, :x1; nocounts=true)
```

where `c~` is the model for counts. `x1` (`projdir`) is the variable to predict. We can then predict with a dataframe as well

```julia
  yhat = predict(m, df, counts)
  yhatnc = predict(m, df, counts; nocounts=true)
```
