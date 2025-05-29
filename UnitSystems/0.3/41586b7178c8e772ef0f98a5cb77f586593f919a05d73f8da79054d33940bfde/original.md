```Julia
kilocalorie(U::UnitSystem) = energy(𝟐^5*𝟓^4*𝟑^2/𝟒𝟑,U,International)
```

Heat energy required to raise 1 kg of water by 1 Kelvin (`kcal`) in `International` units.

```Julia
julia> kilocalorie(International) # J
4186.046511627907

julia> kilocalorie(Metric) # J
4186.737323211057

julia> kilocalorie(English) # ft⋅lb
3087.9789785668913
```
