```
isotope_totaldelta(::Type{IsotopeLinear}, total, delta) -> IsotopeLinear
```

`total` と `delta` から `IsotopeLinear` を作成します

# 例:

```jldoctest; setup = :(import PALEOboxes as PB)
julia> a = PB.isotope_totaldelta(PB.IsotopeLinear, 10.0, -2.0)
(v=10.0, v_moldelta=-20.0, ‰=-2.0)

julia> b = a*2
(v=20.0, v_moldelta=-40.0, ‰=-2.0)

julia> c = a + b
(v=30.0, v_moldelta=-60.0, ‰=-2.0)

julia> PB.get_total(c)
30.0

julia> PB.get_delta(c)
-2.0
```
