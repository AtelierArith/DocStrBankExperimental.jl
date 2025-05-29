```
SimpleRatio(num::Integer, den::Integer)
```

Construct the equivalent of the rational number `num // den`.

Operations with `SimpleRatio` are faster, but also more vulnerable to integer overflow, than with `Rational`. Arithmetic with `SimpleRatio` does not perform any simplification of the resulting ratios. The best defense against overflow is to use ratios with the same denominator: in such cases, `+` and `-` will skip forming the product of denominators. See [`common_denominator`](@ref).

If overflow is a risk, consider constructing them using SaferIntegers.jl.

# Examples

```julia
julia> x, y, z = SimpleRatio(1, 8), SimpleRatio(1, 4), SimpleRatio(2, 8)
(SimpleRatio{Int64}(1, 8), SimpleRatio{Int64}(1, 4), SimpleRatio{Int64}(2, 8))

julia> x+y
SimpleRatio{Int64}(12, 32)

julia> x+z
SimpleRatio{Int64}(3, 8)
```
