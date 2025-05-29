```Julia
radarmile(U::UnitSystem) = 𝟐*nauticalmile(U)/lightspeed(U)
```

Unit of `time` delay from a two-way `nauticalmile` radar return (s).

```Julia
julia> radarmile(Metric)
1.2372115337845802e-5
```
