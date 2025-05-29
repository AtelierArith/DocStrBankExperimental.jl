```
statproduct_league(pd::Species, ivs, league_cp::Int; kwargs...) → level => (cp, statprod)
statproduct_league(name::AbstractString, ivs, league_cp::Int; kwargs...) → level => (cp, statprod)
```

与えられた `ivs` を持つポケモンの `level`、`cp`、および ["ステータスプロダクト"](https://gostadium.club/rank-checker) を、`league_cp` によって許可される限り高くパワーアップしたときに計算します。 [`league_max_level`](@ref) と同じ `kwargs` がサポートされています。
