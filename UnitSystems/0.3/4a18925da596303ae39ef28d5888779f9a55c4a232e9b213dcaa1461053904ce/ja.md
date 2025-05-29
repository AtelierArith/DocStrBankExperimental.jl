```Julia
radarmile(U::UnitSystem) = 𝟐*nauticalmile(U)/lightspeed(U)
```

二方向の `nauticalmile` レーダー反射からの `time` 遅延の単位 (s)。

```Julia
julia> radarmile(Metric)
1.2372115337845802e-5
```
