```julia
VIDAProblem(div, f, lb, ub)

```

Defines a `VIDAProblem` for optimization.

## Arguments

  * `div`: The divergence you wish to fit. This is an instantiation of [`VIDA.AbstractDivergence`](@ref)
  * `f`:   The function that defines the parametric family of templates you will fit. The function        must accept a named tuple as its first argument, whose names define the parameters.
  * `lb`:  A NamedTuple whose names match the argument of `f` and whose values define the lower        bounds of the parameters range you want to search over
  * `lb`: A NamedTuple whose names match the argument of `f` and whose values define the upper        bounds of the parameters range you want to search over

## Example

```julia-repl
julia> f(x) = SlashedGaussianRing(x.σ, x.s)
julia> div = Renyi(img, 0.75)
julia> lb = (x = 0.1, s = 0.001)
julia> ub = (x = 10.0, s = 0.999)
julia> prob = VIDAProblem(div, f, lb, ub)
```
