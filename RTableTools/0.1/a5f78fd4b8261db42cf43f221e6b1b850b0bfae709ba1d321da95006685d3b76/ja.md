```julia
merge(
    x::DataFrames.AbstractDataFrame,
    y::DataFrames.AbstractDataFrame;
    by,
    all,
    all_x,
    all_y,
    makeunique,
    suffixes,
    kw...
) -> Any

```

# 例

```julia
d1 = DataFrame(A=1:3, B=4:6, C=7:9)
d2 = DataFrame(A=1:3, B=4:6, D=7:9)
d = merge(d1, d2, by = "A", suffixes=["_tas", ".rh"])
d[:, "B.rh"]
```

関連: `leftjoin`, `rightjoin`, `innerjoin`, `outerjoin`
