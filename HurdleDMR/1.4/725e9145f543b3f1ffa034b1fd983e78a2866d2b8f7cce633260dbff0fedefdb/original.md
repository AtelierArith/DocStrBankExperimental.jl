```
fit(CIR{HDMR,FM},m,df,counts,projdir[,fmargs...]; <keyword arguments>)
```

Version of fit(CIR{HDMR,FM}...) that takes a @model() and a dataframe instead of a covars matrix, and a projdir::Symbol specifies the dependent variable. See also fit(CIR...).

# Example:

```julia
  m = fit(CIR{HDMR,LinearModel}, @model(h~x1+x2, c~x1), df, counts, :x1; nocounts=true)
```

where `h~` is the model for zeros, `c~` is the model for positives. `x1` (`projdir`) is the variable to predict. We can then predict with a dataframe as well

```julia
  yhat = predict(m, df, counts)
  yhatnc = predict(m, df, counts; nocounts=true)
```
