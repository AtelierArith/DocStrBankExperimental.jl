```
AbstractSingleton{N} <: AbstractHyperrectangle{N}
```

Abstract type for sets with a single value.

### Notes

See [`Singleton`](@ref) for a standard implementation of this interface.

Every concrete `AbstractSingleton` must define the following function:

  * `element(::AbstractSingleton)` – return the single element

Among other functions, the following function is then automatically defined:

  * `element(::AbstractSingleton, i::Int)` – return the single element at index                                           `i`

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractSingleton)
2-element Vector{Any}:
 Singleton
 ZeroSet
```
