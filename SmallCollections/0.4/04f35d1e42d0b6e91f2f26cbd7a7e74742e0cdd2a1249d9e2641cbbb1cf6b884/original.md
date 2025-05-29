```
SmallCollections.MapStyle

MapStyle(f, types::Type...) -> MapStyle
```

A `MapStyle` determines how `SmallCollections` evaluates certain functions like `map` or `findfirst` that take a function `f` as argument. The available subtypes of `MapStyle` are as follows, from the least to the most efficient:

  * `LazyStyle`: the function `f` is only evaluated when strictly necessary, and it is not assumed to be defined for default values. This is the default `MapStyle` for unknown functions.
  * `EagerStyle`: `f` may be evaluated more often than strictly necessary, and it is assumed to be defined for default values. However, it need not map default values to default values.
  * `RigidStyle`: `f` may be evaluated more often than strictly necessary. It is assumed to be defined for default values and to return a default value if all arguments are default values.
  * `StrictStyle`: `f` may be evaluated more often than strictly necessary. It is assumed to be defined for default values and to return a default value if at least one argument is a default value. (This is the same as `RigidStyle` for functions with a single argument.)

The `MapStyle` is predefined for many functions from `Base` as well as for operations that produce new functions out of old. Unnamed functions are not recognized. However, several functions from `SmallCollections` allow to specify a `MapStyle` as keyword argument. In addition, users can define a `MapStyle` for their own types.

See also [`SmallCollections.default`](@ref), [`SmallCollections.isfasttype`](@ref).

# Examples

```jldoctest
julia> using SmallCollections: MapStyle

julia> MapStyle(iszero, Int)   # not RigidStyle: iszero(0) is true, not false
SmallCollections.EagerStyle()

julia> MapStyle(+, Int, Int)
SmallCollections.RigidStyle()

julia> MapStyle(*, Int, Float64)   # not StrictStyle: 0 * Inf is NaN, not 0.0
SmallCollections.RigidStyle()

julia> MapStyle(*, Int, Int)
SmallCollections.StrictStyle()

julia> MapStyle(-, Int)
SmallCollections.StrictStyle()

julia> MapStyle(x -> -x, Int)   # not StrictStyle: anonymous function not recognized
SmallCollections.LazyStyle()

julia> MapStyle(-, Int128)   # Int128 is not a fast type, so better be lazy
SmallCollections.LazyStyle()

julia> MapStyle(isfinite∘inv, Float64)   # function composition is recognized
SmallCollections.EagerStyle()

julia> MapStyle(!iszero, Int)   # function composition again
SmallCollections.EagerStyle()

julia> MapStyle(>=(1), Int)   # >=(1) is Base.Fix2(>=, 1), which is recognized
SmallCollections.EagerStyle()
```
