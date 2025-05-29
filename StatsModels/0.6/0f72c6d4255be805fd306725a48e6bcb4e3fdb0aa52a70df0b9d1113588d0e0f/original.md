```
concrete_term(t::Term, data[, hint])
```

Create concrete term from the placeholder `t` based on a data source and optional hint.  If `data` is a table, the `getproperty` is used to extract the appropriate column.

The `hint` can be a `Dict{Symbol}` of hints, or a specific hint, a concrete term type (`ContinuousTerm` or `CategoricalTerm`), or an instance of some `<:AbstractContrasts`, in which case a `CategoricalTerm` will be created using those contrasts.

If no hint is provided (or `hint==nothing`), the `eltype` of the data is used: `Number`s are assumed to be continuous, and all others are assumed to be categorical.

# Example

```jldoctest
julia> concrete_term(term(:a), [1, 2, 3])
a(continuous)

julia> concrete_term(term(:a), [1, 2, 3], nothing)
a(continuous)

julia> concrete_term(term(:a), [1, 2, 3], CategoricalTerm)
a(DummyCoding:3→2)

julia> concrete_term(term(:a), [1, 2, 3], EffectsCoding())
a(EffectsCoding:3→2)

julia> concrete_term(term(:a), [1, 2, 3], Dict(:a=>EffectsCoding()))
a(EffectsCoding:3→2)

julia> concrete_term(term(:a), (a = [1, 2, 3], b = [0.0, 0.5, 1.0]))
a(continuous)
```
