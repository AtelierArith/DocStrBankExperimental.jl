```
OffsetArray(A, indices...)
```

最初の引数と要素の型とサイズを共有する `AbstractArray` を返しますが、提供された `indices` を使用してその軸を推測します。すべてのインデックスが `AbstractUnitRange` の場合、これらは各次元に沿った軸の範囲として直接使用されます。他の許可される型については、以下の例を参照してください。

また、配列の一つの隅の座標を指定し、`A` のサイズから軸を自動的に計算させることも可能です。このコンストラクタは、C や Python などの言語での配列に続くゼロベースのインデックス付けスキームに沿って、各軸に沿った任意の開始インデックスにシフトするのに便利です。これに関する使用法については、[`Origin`](@ref) と以下の例を参照してください。

# 例: オフセット

`indices` には整数と範囲のような型の2種類があります。

整数はオフセットとして認識され、`0` はオフセットが適用されないことを意味します：

```jldoctest; setup=:(using OffsetArrays)
julia> A = OffsetArray(reshape(1:6, 2, 3), -1, -2)
2×3 OffsetArray(reshape(::UnitRange{Int64}, 2, 3), 0:1, -1:1) with eltype Int64 with indices 0:1×-1:1:
 1  3  5
 2  4  6

julia> A[0, 1]
5
```

範囲のような型の例には、`UnitRange`（例: `-1:2`）、`CartesianIndices`、および `Colon()`（または簡潔に `:`）があります。`UnitRange` は特定の次元に沿った軸の範囲を指定し、`CartesianIndices` は複数の次元に沿った軸の範囲を指定し、`Colon` はその次元に沿って `OffsetArray` が親と軸を共有することを示すプレースホルダーです。

```jldoctest; setup=:(using OffsetArrays)
julia> OffsetArray(reshape(1:6, 2, 3), 0:1, -1:1)
2×3 OffsetArray(reshape(::UnitRange{Int64}, 2, 3), 0:1, -1:1) with eltype Int64 with indices 0:1×-1:1:
 1  3  5
 2  4  6

julia> OffsetArray(reshape(1:6, 2, 3), :, -1:1) # : は最初の次元にオフセットを適用しないことを示すプレースホルダー
2×3 OffsetArray(reshape(::UnitRange{Int64}, 2, 3), 1:2, -1:1) with eltype Int64 with indices 1:2×-1:1:
 1  3  5
 2  4  6
```

`CartesianIndices` を使用して、対角線上の2つの隅の座標を指定します：

```jldoctest; setup=:(using OffsetArrays)
julia> OffsetArray(reshape(1:6, 2, 3), CartesianIndex(0, -1):CartesianIndex(1, 1))
2×3 OffsetArray(reshape(::UnitRange{Int64}, 2, 3), 0:1, -1:1) with eltype Int64 with indices 0:1×-1:1:
 1  3  5
 2  4  6
```

整数と範囲のような型は同じ呼び出しで組み合わせることはできません：

```julia
julia> OffsetArray(reshape(1:6, 2, 3), 0, -1:1)
ERROR: [...]
```

# 例: 原点

[`OffsetArrays.Origin`](@ref) を使用して、OffsetArray の原点を指定することができます。ここでの原点という用語は、`AbstractVector` の左端、`AbstractMatrix` の左下隅など、座標の最小値を持つ隅を指します。原点の座標は、各次元に沿った配列の開始インデックスを設定します。

```jldoctest; setup=:(using OffsetArrays)
julia> a = [1 2; 3 4];

julia> OffsetArray(a, OffsetArrays.Origin(0, 1))
2×2 OffsetArray(::Matrix{Int64}, 0:1, 1:2) with eltype Int64 with indices 0:1×1:2:
 1  2
 3  4

julia> OffsetArray(a, OffsetArrays.Origin(0)) # 各次元に沿った原点をゼロに設定
2×2 OffsetArray(::Matrix{Int64}, 0:1, 0:1) with eltype Int64 with indices 0:1×0:1:
 1  2
 3  4
```
