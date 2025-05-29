```
factorproduct(facs...)
```

Return a `Vector{NamedTuple}` obtained by crossing `facs...`.

The arguments should be coerceable to a `Tables.RowTable` with `rowtable`.

The value is a `Tables.RowTable` and hence can be converted to a `DataFrame`.

# Example

```julia-repl
julia> DataFrame(factorproduct((item=nlevels(3,'I'),), (subj=nlevels(5), age=["Y","Y","Y","O","O"])))
15×3 DataFrame
│ Row │ item   │ subj   │ age    │
│     │ String │ String │ String │
├─────┼────────┼────────┼────────┤
│ 1   │ I1     │ S1     │ Y      │
│ 2   │ I2     │ S1     │ Y      │
│ 3   │ I3     │ S1     │ Y      │
│ 4   │ I1     │ S2     │ Y      │
│ 5   │ I2     │ S2     │ Y      │
│ 6   │ I3     │ S2     │ Y      │
│ 7   │ I1     │ S3     │ Y      │
│ 8   │ I2     │ S3     │ Y      │
│ 9   │ I3     │ S3     │ Y      │
│ 10  │ I1     │ S4     │ O      │
│ 11  │ I2     │ S4     │ O      │
│ 12  │ I3     │ S4     │ O      │
│ 13  │ I1     │ S5     │ O      │
│ 14  │ I2     │ S5     │ O      │
│ 15  │ I3     │ S5     │ O      │
```
