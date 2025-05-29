```Julia
nauticalmile(U::UnitSystem) = greatcircle(U)/𝟐^5/𝟑^3/𝟓^2
```

Standard `nauticalmile` as defined by `earthradius` (m or ft).

```Julia
julia> nauticalmile(Metric) # m
1854.5334338961468

julia> nauticalmile(Meridian) # em
1851.8518518518517

julia> nauticalmile(English) # ft
6084.427276562163
```
