```Julia
parsec(U::UnitSystem) = astronomicalunit(U)*𝟐^2*𝟑^4*𝟓^3/τ
```

長さの単位は、1 `astronomicalunit` が1アークセカンドの角度を subtends する時に定義されます。

```Julia
julia> parsec(Metric) # m
3.085677581491367e16

julia> parsec(English) # ft
1.0123614112504485e17

julia> parsec(IAU) # au
206264.80624709636
```
