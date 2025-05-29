```
tlag(tv, xv, n = oneunit(tv[1] - tv[1]); checksorted=true)
```

Lag vector `xv` by `n` with respect to time vector `tv`. Gaps in `tv` is allowed.

The type of `n` should be consistent with `tv` for arithmetic. For example,  if `tv` is a Date vector, then `n` should be a `Period` e.g. `Day(2)`. By default,  `n` is set as the unitary difference in `tv`.

Time vector `tv` has to be strictly increasing. This requirement is checked by default.  Users can turn off this behavior for performance-sensitive codes by  setting `checksorted=false`.

# Examples

```jldoctest
julia> tlag([1;2;4], [4,5,6], 1)
3-element Vector{Union{Missing, Int64}}:
  missing
 4
  missing
```

```jldoctest
julia> tlag([Date(2020);Date(2022);Date(2024)], [4,5,6], Year(2))
3-element Vector{Union{Missing, Int64}}:
  missing
 4
 5
```

See also `tlead`, `tshift`.
