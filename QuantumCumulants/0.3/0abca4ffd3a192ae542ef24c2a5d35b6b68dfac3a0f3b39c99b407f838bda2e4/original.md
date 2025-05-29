```
NLevelSpace <: HilbertSpace
NLevelSpace(name::Symbol,levels,GS=levels[1])
```

Define a [`HilbertSpace`](@ref) for an object consisting of `N` discrete energy levels. The given `levels` must be an integer specifying the number of levels, or an iterable collection of levels. The argument `GS` specifies which state should be treated as ground state and is rewritten using population conservation during simplification. See also: [`Transition`](@ref)

# Examples:

```
julia> ha = NLevelSpace(:a,3)
ℋ(a)

julia> ha = NLevelSpace(:a,(:g,:e))
ℋ(a)
```
