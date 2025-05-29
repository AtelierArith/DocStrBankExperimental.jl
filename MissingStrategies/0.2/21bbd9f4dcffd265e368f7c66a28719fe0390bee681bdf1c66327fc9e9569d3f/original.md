```
handlemissings(fun, ...)
```

Creates an expression that defines new methods that allow missings in the  eltype of an argument.

# Arguments

  * `fun`: Expression of a function to extend
  * `pos_missing = 1`: The postition of the argument that should handle missings
  * `pos_strategy = pos_missing + 1`: The position at which the argument of MissingStrategy  is to be inserted into the function signature
  * `type_missing = :Any`: The new type of the argument that should handle missings.  This can be an expression of the value.
  * `defaultstrategy::Union{Nothing,MissingStrategy} = :nothing`: the value of the default  of the strategy argument. Use `:nothing` to indicate not specifying a default value. This can be an expression of the value.
  * `gens = ()`: Tuple of generator functions (see [mgen]{@ref})
  * `argname_strategy = :ms`: symbol of the argument name of the strategy argument
  * `suffix="_hm"`: attached to the name of the dispatching function to avoid method ambiguities

Ususually this function is called from a macro that povide suitable dfault values

  * [`@handlemissings_typed`](@ref) suitable if the type of the original method does not allow missing value
  * [`@handlemissings_any`](@ref) suitable if the type of the original method does allow missing value.
  * [`@handlemissings_stub`](@ref) suitable for writing user-specified handling routines.
