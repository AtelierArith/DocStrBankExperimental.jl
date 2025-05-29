```
copy(xf::Transducer, T, foldable) :: Union{T, Empty{T}}
copy(xf::Transducer, foldable::T) :: Union{T, Empty{T}}
copy([T,] eduction::Eduction) :: Union{T, Empty{T}}
```

トランスデューサ `xf` を使って `foldable` を処理し、その結果で満たされたタイプ `T` のコンテナを作成します。トランスデューサが何も生成しない場合は [`BangBang.Empty{T}`](https://juliafolds.github.io/BangBang.jl/dev/#BangBang.NoBang.Empty) を返します。 （これは、タイプに基づいて空のコンテナを作成するための一貫したインターフェースがないためであり、すべてのコンテナが空のコンテナを作成することをサポートしているわけではありません。）

並列バージョンについては、[`tcopy`](@ref) と [`dcopy`](@ref) を参照してください。

!!! compat "Transducers.jl 0.4.4"
    バージョン 0.4.4 で新機能です。


!!! compat "Transducers.jl 0.4.8"
    `copy` は現在、エデュクションを受け入れます。


# 例

```jldoctest
julia> using Transducers
       using BangBang: Empty

julia> copy(Map(x -> x => x^2), Dict, 2:2)
Dict{Int64, Int64} with 1 entry:
  2 => 4

julia> @assert copy(Filter(_ -> false), Set, 1:1) === Empty(Set)

julia> using TypedTables

julia> @assert copy(Map(x -> (a=x, b=x^2)), Table, 1:1) == Table(a=[1], b=[1])

julia> using StructArrays

julia> @assert copy(Map(x -> (a=x, b=x^2)), StructVector, 1:1) == StructVector(a=[1], b=[1])

julia> using DataFrames

julia> @assert copy(
           Map(x -> (A = x.a + 1, B = x.b + 1)),
           DataFrame(a = [1], b = [2]),
       ) == DataFrame(A = [2], B = [3])
```
