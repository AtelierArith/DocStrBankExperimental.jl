```
GapObj(input, recursion_dict::GapCacheDict = nothing; recursive::Bool = false)
GapObj(input, recursive::Bool = false)
```

One can use the type [`GapObj`](@ref) as a constructor, in order to convert the julia object `input` to an appropriate GAP object.

If `recursive` is set to `true`, recursive conversion of nested Julia objects (arrays, tuples, and dictionaries) is performed.

The input `recursion_dict` should never be set by the user, it is meant to keep egality of input data, by converting equal data to identical objects in GAP.

# Examples

```jldoctest
julia> GapObj(1//3)
GAP: 1/3

julia> GapObj("abc")
GAP: "abc"

julia> GapObj([1 2; 3 4])
GAP: [ [ 1, 2 ], [ 3, 4 ] ]

julia> GapObj([[1, 2], [3, 4]])
GAP: [ <Julia: [1, 2]>, <Julia: [3, 4]> ]

julia> GapObj([[1, 2], [3, 4]], true)
GAP: [ [ 1, 2 ], [ 3, 4 ] ]

julia> GapObj([[1, 2], [3, 4]], recursive = true)
GAP: [ [ 1, 2 ], [ 3, 4 ] ]
```

Note that this conversion is *not* restricted to outputs that actually are of type `GapObj`, also GAP integers, finite field elements, and booleans can be created by the constructor `GapObj`.

```jldoctest
julia> res = GapObj(42);  res isa GapObj
false

julia> res isa GAP.Obj
true
```

The following `GapObj` conversions are supported by GAP.jl. (Other Julia packages may provide conversions for more Julia objects.)

|                           Julia type |   GAP filter |
| ------------------------------------:| ------------:|
|       `Int8`, `Int16`, ..., `BigInt` |      `IsInt` |
|                                `FFE` |      `IsFFE` |
|                               `Bool` |     `IsBool` |
|                        `Rational{T}` |      `IsRat` |
|      `Float16`, `Float32`, `Float64` |    `IsFloat` |
|                     `AbstractString` |   `IsString` |
|                             `Symbol` |   `IsString` |
|                               `Char` |     `IsChar` |
|                          `Vector{T}` |     `IsList` |
|          `Vector{Bool}`, `BitVector` |    `IsBList` |
|                             `Set{T}` |     `IsList` |
|                           `Tuple{T}` |     `IsList` |
|                          `Matrix{T}` |     `IsList` |
| `Dict{String, T}`, `Dict{Symbol, T}` |   `IsRecord` |
|    `UnitRange{T}`, `StepRange{T, S}` |    `IsRange` |
|                           `Function` | `IsFunction` |
