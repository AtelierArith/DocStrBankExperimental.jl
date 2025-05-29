```
differential(variables::Node...)
```

Returns an anonymous function that takes the derivative of a scalar function with respect to `variables`.

# Example

```julia
julia> @variables t
t

julia> f = t^2
(t ^ 2)

julia> Dt = differential(t)      
#69 (generic function with 1 method)

julia> Dt(f)
(2 * t)

julia> Dt = differential(t,t)    
#69 (generic function with 1 method)

julia> Dt(f)
2
```
