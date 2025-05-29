```Julia
parsec(U::UnitSystem) = astronomicalunit(U)*𝟐^2*𝟑^4*𝟓^3/τ
```

Unit of `length` defined at which 1 `astronomicalunit` subtends an angle of 1 arcsecond.

```Julia
julia> parsec(Metric) # m
3.085677581491367e16

julia> parsec(English) # ft
1.0123614112504485e17

julia> parsec(IAU) # au
206264.80624709636
```
