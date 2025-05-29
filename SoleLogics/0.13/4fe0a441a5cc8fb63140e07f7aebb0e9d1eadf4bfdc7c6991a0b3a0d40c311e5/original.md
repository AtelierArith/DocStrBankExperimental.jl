```
abstract type AbstractRelation end
```

Abstract type for the relations of a multi-modal annotated accessibility graph (Kripke structure). Two noteworthy relations are `identityrel` and `globalrel`, which access the current world and all worlds, respectively.

# Examples

```julia-repl
julia> fr = SoleLogics.FullDimensionalFrame((10,), Interval{Int});

julia> Interval(8,11) in (accessibles(fr, Interval(2,5), IA_L))
true
```

# Implementation

When implementing a new relation type `R`, please provide the methods:

```
arity(::R)::Int = ...
syntaxstring(::R; kwargs...)::String = ...
```

If the relation is symmetric, please specify its converse relation `cr` with:

```
hasconverse(::R) = true
converse(::R) = cr
```

If the relation is many-to-one or one-to-one, please flag it with:

```
istoone(::R) = true
```

If the relation is reflexive or transitive, flag it with:

```
isreflexive(::R) = true
istransitive(::R) = true
```

Most importantly, the logical semantics for `R` should be defined via `accessibles` methods; refer to the help for `accessibles`.

See also [`issymmetric`](@ref), [`isreflexive`](@ref), [`istransitive`](@ref), [`isgrounding`](@ref), [`arity`](@ref), [`syntaxstring`](@ref), [`converse`](@ref), [`hasconverse`](@ref), [`istoone`](@ref), [`identityrel`](@ref), [`globalrel`](@ref), [`accessibles`](@ref), [`AbstractKripkeStructure`](@ref), [`AbstractFrame`](@ref), [`AbstractWorld`](@ref).
