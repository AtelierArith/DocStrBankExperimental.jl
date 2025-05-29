```
aaa(y, z)
aaa(f)
```

Adaptively compute a rational interpolant.

# Arguments

## discrete mode

  * `y::AbstractVector{<:Number}`: values at nodes
  * `z::AbstractVector{<:Number}`: interpolation nodes

## continuous mode

  * `f::Function`: function to approximate on the interval [-1,1]

# Keyword arguments

  * `max_degree::Integer=150`: maximum numerator/denominator degree to use
  * `float_type::Type=Float64`: floating point type to use for the computation
  * `tol::Real=1000*eps(float_type)`: tolerance for stopping
  * `stagnation::Integer=10`: number of iterations to determines stagnation
  * `stats::Bool=false`: return convergence statistics

# Returns

  * `r::Barycentric`: the rational interpolant
  * `stats::NamedTuple`: convergence statistics, if keyword `stats=true`

# Examples

```julia-repl
julia> z = 1im * range(-10, 10, 500);

julia> y = @. exp(z);

julia> r = aaa(z, y);

julia> degree(r)   # both numerator and denominator
12

julia> first(nodes(r), 4)
4-element Vector{ComplexF64}:
 0.0 - 6.272545090180361im
 0.0 + 9.43887775551102im
 0.0 - 1.1022044088176353im
 0.0 + 4.909819639278557im

julia> r(1im * π / 2)
-2.637151617496356e-15 + 1.0000000000000002im
```

See also [`approximate`](@ref) for approximating a function on a curve or region.
