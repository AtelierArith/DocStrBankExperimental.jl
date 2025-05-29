```
scitype(X)
```

The scientific type (interpretation) of `X`, as distinct from its machine type. Atomic scientific types (`Continuous`, `Multiclass`, etc) are mostly abstract types defined in the package ScientificTypesBase.jl. Scientific types do not ordinarily have instances.

### Examples

```
julia> scitype(3.14)
Continuous

julia> scitype([1, 2, missing])
AbstractVector{Union{Missing, Count}}

julia> scitype((5, "beige"))
Tuple{Count, Textual}

julia> using CategoricalArrays

julia> table = (gender = categorical(['M', 'M', 'F', 'M', 'F']),
     ndevices = [1, 3, 2, 3, 2])

julia> scitype(table)
Table{Union{AbstractVector{Count}, AbstractVector{Multiclass{2}}}}

```

Column scitpes of a table can also be inspected with [`schema`](@ref).

The behavior of `scitype` is detailed in the [ScientificTypes documentation](https://juliaai.github.io/ScientificTypes.jl/dev/#Summary-of-the-default-convention). Key features of the default behavior are:

  * `AbstractFloat` has scitype as `Continuous <: Infinite`.
  * Any `Integer` has scitype as `Count <: Infinite`.
  * Any `CategoricalValue` `x` has scitype as `Multiclass <: Finite` or `OrderedFactor <: Finite`, depending on the value of `isordered(x)`.
  * `String`s and `Char`s do *not* have scitype `Multiclass` or `OrderedFactor`; they have scitypes `Textual` and `Unknown` respectively.
  * The scientific types of `nothing` and `missing` are `Nothing` and `Missing`, Julia types that are also regarded as scientific.

!!! note
    Third party packages may extend the behavior of `scitype`: Objects previously having `Unknown` scitype may no longer do so.


See also [`coerce`](@ref), [`autotype`](@ref), [`schema`](@ref).
