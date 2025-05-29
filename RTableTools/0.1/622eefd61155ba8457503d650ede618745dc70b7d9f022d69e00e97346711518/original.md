```
fwrite(df, file; kw...)
```

```julia
df = DataFrame(A=1:3, B=4:6, C=7:9)
fwrite(df, "a.csv")
fwrite(df, "a.csv", append=true)
```
