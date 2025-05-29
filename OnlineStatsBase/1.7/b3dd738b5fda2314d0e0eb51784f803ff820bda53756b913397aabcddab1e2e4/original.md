```
fit!(stat::OnlineStat, data)
```

Update the "sufficient statistics" of a `stat` with more data.   If `typeof(data)` is not the type of a single observation for the provided `stat`, `fit!` will attempt to iterate through and `fit!` each item in `data`.  Therefore, `fit!(Mean(), 1:10)` translates roughly to:

```julia
o = Mean()

for x in 1:10
    fit!(o, x)
end
```
