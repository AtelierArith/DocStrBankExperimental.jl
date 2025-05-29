```
approximate(f, domain)
```

Adaptively compute a rational interpolant on a continuous or discrete domain.

# Arguments

## Continuous domain

  * `f::Function`: function to approximate
  * `domain`: curve, path, or region from ComplexRegions

## Discrete domain

  * `f::Function`: function to approximate
  * `z::AbstractVector`: point set on which to approximate

# Keywords

  * `max_iter::Integer=150`: maximum number of iterations on node addition
  * `float_type::Type`: floating point type to use for the computation¹
  * `tol::Real=1000*eps(float_type)`: relative tolerance for stopping
  * `allowed::Function`: function to determine if a pole is allowed²
  * `refinement::Integer=3`: number of test points between adjacent nodes (continuum only)
  * `stagnation::Integer=20`: number of iterations to determine stagnation

¹Default of `float_type` is the promotion of `float(1)` and the float type of the domain. ²Default is to disallow poles on the curve or in the interior of a continuous domain, or to accept all poles on a discrete domain. Use `allowed=true` to allow all poles.

# Returns

  * `r::Approximation`: the rational interpolant

See also [`Approximation`](@ref), [`check`](@ref), [`rewind`](@ref).

# Examples

```julia-repl
julia> f = x -> tanh( 40*(x - 0.15) );

julia> r = approximate(f, unit_interval)
Barycentric{Float64, Float64} rational function of type (22, 22) on the domain: Path{Float64} with 1 curve

julia> ( r(0.3), f(0.3) )
(0.9999877116508015, 0.9999877116507956)

julia> check(r);   # accuracy over the domain
[ Info: Max error is 1.58e-13
```
