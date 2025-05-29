```
isguaranteed(x::BareInterval)
isguaranteed(x::Interval)
isguaranteed(x::Complex{<:Interval})
```

Test whether the interval is not guaranteed to encompass all possible numerical errors. This happens whenever an [`Interval`](@ref) is constructed using `convert(::Type{<:Interval}, ::Real)`, which may occur implicitly when mixing intervals and `Real` types.

Since conversion between `BareInterval` and `Number` is prohibited, this implies that `isguaranteed(::BareInterval) == true`.

In the case of a complex interval `x`, this is semantically equivalent to `isguaranteed(real(x)) & isguaranteed(imag(x))`.

# Examples

```jldoctest
julia> isguaranteed(bareinterval(1))
true

julia> isguaranteed(interval(1))
true

julia> isguaranteed(convert(Interval{Float64}, 1))
false

julia> isguaranteed(interval(1) + 0)
false
```
