```
Verbosity
```

A flag that determine what logging statements are shown during [`speculate`](@ref).

This is modelled as a set, where [`silent`](@ref) is the empty set. The non-empty component flags are [`debug`](@ref), [`review`](@ref), and [`warn`](@ref).

# Interface

This type implements part of the `AbstractSet` interface.

  * `intersect(::Verbosity, ::Verbosity...)`
  * `isdisjoint(::Verbosity, ::Verbosity)`
  * `isempty(::Verbosity)`
  * `issetequal(::Verbosity, ::Verbosity)`
  * `issubset(::Verbosity, ::Verbosity)`
  * `setdiff(::Verbosity, ::Verboosity...)`
  * `show(::IO, ::Verbosity)`
  * `symdiff(::Verbosity, ::Verbosity...)`
  * `union(::Verbosity, ::Verbosity...)`

# Examples

```jldoctest
julia> silent
silent::Verbosity

julia> debug ∪ review
(debug ∪ review)::Verbosity

julia> debug ⊆ debug ∪ review
true

julia> debug ⊆ warn
false
```
