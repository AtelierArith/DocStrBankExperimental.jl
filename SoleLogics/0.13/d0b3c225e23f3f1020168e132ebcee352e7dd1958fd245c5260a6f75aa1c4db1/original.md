```
struct FunctionalWorldFilter{W <: AbstractWorld, F <: Function} <: WorldFilter{W}
	filter::FunctionWrapper{Bool, Tuple{W}}
end
```

A world filter based on a function from `AbstractWorld` to `Bool`.

# Constructors

  * `FunctionalWorldFilter{W, F}(filter::FunctionWrapper{Bool, Tuple{W}}) where {W <: AbstractWorld, F <: Function}`
  * `FunctionalWorldFilter(filter::FunctionWrapper{Bool, Tuple{W}}, functiontype::Type{F}) where {W <: AbstractWorld, F <: Function}`
  * `FunctionalWorldFilter{W, F}(filter::F) where {W <: AbstractWorld, F <: Function}`
  * `FunctionalWorldFilter{W}(filter::F) where {W <: AbstractWorld, F <: Function}`
  * `FunctionalWorldFilter(filter::F, worldtype::Type{W}) where {W <: AbstractWorld, F <: Function}`

See also [`filterworlds`](@ref), [`FilteredRelation`](@ref).
