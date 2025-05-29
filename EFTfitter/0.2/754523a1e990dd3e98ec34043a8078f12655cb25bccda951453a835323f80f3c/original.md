```
struct Correlation
```

Fields:  

  * `matrix::Array{Float64, 2}`: Observables that are measured.
  * `active::Bool`: Use this uncertainty category in fit. Defaults to `true`.

Constructors:

```julia
Correlation(matrix::Array{<:Real, 2}; active::Bool = true)
```
