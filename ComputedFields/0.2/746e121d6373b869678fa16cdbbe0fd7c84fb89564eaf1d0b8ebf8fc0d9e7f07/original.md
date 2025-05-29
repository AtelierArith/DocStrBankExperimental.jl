```
@computed mutable struct [...] end
```

Automatically recompute fields. 

Fields can be assigned an expression with `=` that is reevaluated when one of the variables in that expression is set.

# Example

```jldocs
julia> @computed mutable struct SinCos
    x::Float64
    thesincos::Tuple{Float64,Float64} = sincos(x)
end

julia> sc = SinCos(0.0)
SinCos(0.0, (0.0, 1.0))

julia> sc.x = pi/2
1.5707963267948966

julia> sc.thesincos
(1.0, 6.123233995736766e-17)
```
