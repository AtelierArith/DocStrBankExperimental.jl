```
(x::OutputVar)(target_coord)
```

Interpolate variable `x` onto the given `target_coord` coordinate using multilinear interpolation.

Extrapolation is now allowed and will throw a `BoundsError` in most cases.

If any element of the arrays of the dimensions is a Dates.DateTime, then interpolation is not possible. Interpolations.jl do not support making interpolations for dates. If the longitudes span the entire range and are equispaced, then a periodic boundary condition is added for the longitude dimension. If the latitudes span the entire range and are equispaced, then a flat boundary condition is added for the latitude dimension. In all other cases, an error is thrown when extrapolating outside of the array of the dimension.

# Example

```jldoctest
julia> import ClimaAnalysis;

julia> time = 100.0:110.0 |> collect;

julia> z = 0.0:20.0 |> collect;

julia> data = reshape(1.0:(11 * 21), (11, 21));

julia> var2d = ClimaAnalysis.OutputVar(Dict("time" => time, "z" => z), data); var2d.([[105., 10.], [105.5, 10.5]])
2-element Vector{Float64}:
 116.0
 122.0
```
