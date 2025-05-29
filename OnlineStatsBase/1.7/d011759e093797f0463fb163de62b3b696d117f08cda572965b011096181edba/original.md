```
fit!(stat::OnlineStat, y, n)
```

Update the "sufficient statistics" of a `stat` with multiple observations of a single value. Unless a specialized formula is used, `fit!(Mean(), 10, 5)` is equivalent to:

```julia
o = Mean()

for _ in 1:5
    fit!(o, 10)
end
```
