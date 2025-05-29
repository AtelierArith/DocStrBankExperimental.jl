```
PolyharmonicSpline(data::DataFrame, k::Int64, output::Symbol)
```

Creates a polyharmonic spline that is trained by given data.

#Examples

```jldoctest
julia> data = DataFrame(x = 1:10, y = [1, -5, -10, -12, -8, -1, 5, 12, 23, 50]);

julia> PolyharmonicSpline(data, 2, :y) |> DisplayAs.withcontext(:compact => true)
PolyharmonicSpline([1.14733, -0.449609, 0.0140379, -1.02859, -0.219204, 0.900367, 0.00895592, 1.07145, -5.33101, 3.88628], [-112.005, 6.84443], [1.0; 2.0; … ; 9.0; 10.0;;], 2, [:x], :y)
```
