```
castCodata(year::Int)
```

Method to create the [`Codata`](@ref) object

#### Example:

```
julia> codata = castCodata(2022);

julia> strValue.([codata.∆νCs,codata.c,codata.h])
3-element Vector{String}:
 "9192631770 Hz"
 "299792458 m s⁻¹"
 "6.62607e-34 J Hz⁻¹"
```
