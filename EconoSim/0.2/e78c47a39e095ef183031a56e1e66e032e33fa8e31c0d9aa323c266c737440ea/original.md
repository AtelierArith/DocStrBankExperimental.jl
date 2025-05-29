```
make_tiers(dem_settings::Vector{T}) where  {T <: Tuple{Real, Real}}
```

Convert the vector of tuples into DemTiers. The first interval always starts with 0, the last interval always has an unbounded upper bound. Tiers are sorted from low to high.
