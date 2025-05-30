```
@opt_out frule([config], _, f, args...)
@opt_out rrule([config], f, args...)
```

This allows you to opt-out of an `frule` or an `rrule` by providing a more specific method, that says to use the AD system to differentiate it.

For example, consider some function `foo(x::AbtractArray)`. In general, you know an efficient and generic way to implement its `rrule`. You do so, (likely making use of [`ProjectTo`](@ref)). But it actually turns out that for some `FancyArray` type it is better to let the AD do its thing.

Then you would write something like:

```julia
function rrule(::typeof(foo), x::AbstractArray)
    foo_pullback(ȳ) = ...
    return foo(x), foo_pullback
end

@opt_out rrule(::typeof(foo), ::FancyArray)
```

This will generate an [`rrule`](@ref) that returns `nothing`, and will also add a similar entry to [`ChainRulesCore.no_rrule`](@ref).

Similar applies for [`frule`](@ref) and [`ChainRulesCore.no_frule`](@ref)

For more information see the [documentation on opting out of rules](@ref opt_out).
