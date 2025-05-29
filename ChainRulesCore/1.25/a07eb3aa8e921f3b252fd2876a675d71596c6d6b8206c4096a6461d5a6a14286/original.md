```
rrule([::RuleConfig,] f, x...)
```

Expressing `x` as the tuple `(x₁, x₂, ...)` and the output tuple of `f(x...)` as `Ω`, return the tuple:

```julia
(Ω, (Ω̄₁, Ω̄₂, ...) -> (s̄elf, x̄₁, x̄₂, ...))
```

Where the second return value is the the propagation rule or pullback. It takes in cotangents corresponding to the outputs (`x̄₁, x̄₂, ...`), and `s̄elf`, the internal values of the function itself (for closures)

If no method matching `rrule(f, xs...)` has been defined, then return `nothing`.

Examples:

unary input, unary output scalar function:

```jldoctest
julia> x = rand();

julia> sinx, sin_pullback = rrule(sin, x);

julia> sinx == sin(x)
true

julia> sin_pullback(1) == (NoTangent(), cos(x))
true
```

binary input, unary output scalar function:

```jldoctest
julia> x, y = rand(2);

julia> hypotxy, hypot_pullback = rrule(hypot, x, y);

julia> hypotxy == hypot(x, y)
true

julia> hypot_pullback(1) == (NoTangent(), (x / hypot(x, y)), (y / hypot(x, y)))
true
```

The optional [`RuleConfig`](@ref) option allows specifying rrules only for AD systems that support given features. If not needed, then it can be omitted and the `rrule` without it will be hit as a fallback. This is the case for most rules.

See also: [`frule`](@ref), [`@scalar_rule`](@ref), [`RuleConfig`](@ref)
