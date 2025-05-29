```
GapObj(input, recursion_dict::GapCacheDict = nothing; recursive::Bool = false)
GapObj(input, recursive::Bool = false)
```

型 [`GapObj`](@ref) をコンストラクタとして使用することで、julia オブジェクト `input` を適切な GAP オブジェクトに変換できます。

`recursive` が `true` に設定されている場合、ネストされた Julia オブジェクト（配列、タプル、辞書）の再帰的な変換が行われます。

入力 `recursion_dict` はユーザーによって設定されるべきではなく、等しいデータを GAP 内で同一のオブジェクトに変換するために使用されます。

# 例

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

この変換は、実際に `GapObj` 型である出力に制限されているわけではなく、GAP 整数、有限体の要素、およびブール値もコンストラクタ `GapObj` によって作成できます。

```jldoctest
julia> res = GapObj(42);  res isa GapObj
false

julia> res isa GAP.Obj
true
```

次の `GapObj` 変換は GAP.jl によってサポートされています。（他の Julia パッケージは、より多くの Julia オブジェクトの変換を提供する場合があります。）

|                              Julia 型 |     GAP フィルタ |
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
