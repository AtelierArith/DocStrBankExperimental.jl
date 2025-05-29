```
castCodata(year::Int)
```

[`Codata`](@ref) オブジェクトを作成するためのメソッド

#### 例:

```
julia> codata = castCodata(2022);

julia> strValue.([codata.∆νCs,codata.c,codata.h])
3-element Vector{String}:
 "9192631770 Hz"
 "299792458 m s⁻¹"
 "6.62607e-34 J Hz⁻¹"
```
