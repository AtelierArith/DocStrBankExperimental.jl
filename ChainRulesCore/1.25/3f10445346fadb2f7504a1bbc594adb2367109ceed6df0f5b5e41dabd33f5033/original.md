```
frule([::RuleConfig,] (Δf, Δx...), f, x...)
```

Expressing the output of `f(x...)` as `Ω`, return the tuple:

```julia
(Ω, ΔΩ)
```

The second return value is the tangent w.r.t. the output.

If no method matching `frule((Δf, Δx...), f, x...)` has been defined, then return `nothing`.

Examples:

unary input, unary output scalar function:

```jldoctest frule
julia> dself = NoTangent();

julia> x = rand()
0.8236475079774124

julia> sinx, Δsinx = frule((dself, 1), sin, x)
(0.7336293678134624, 0.6795498147167869)

julia> sinx == sin(x)
true

julia> Δsinx == cos(x)
true
```

Unary input, binary output scalar function:

```jldoctest frule
julia> sincosx, Δsincosx = frule((dself, 1), sincos, x);

julia> sincosx == sincos(x)
true

julia> Δsincosx[1] == cos(x)
true

julia> Δsincosx[2] == -sin(x)
true
```

Note that techically speaking julia does not have multiple output functions, just functions that return a single output that is iterable, like a `Tuple`. So this is actually a [`Tangent`](@ref):

```jldoctest frule
julia> Δsincosx
Tangent{Tuple{Float64, Float64}}(0.6795498147167869, -0.7336293678134624)
```

The optional [`RuleConfig`](@ref) option allows specifying frules only for AD systems that support given features. If not needed, then it can be omitted and the `frule` without it will be hit as a fallback. This is the case for most rules.

See also: [`rrule`](@ref), [`@scalar_rule`](@ref), [`RuleConfig`](@ref)
