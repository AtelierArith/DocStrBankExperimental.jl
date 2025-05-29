```
bits(v::SmallCollections.AbstractFixedVector{N,T}) where {N, T <: Union{Base.BitInteger,Bool,Char,Enum}} -> Unsigned
```

与えられたベクターを符号なし整数に変換します。

ビット整数、`Char` および `Enum` 型の場合、これは `reinterpret(U, Tuple(v))` と同じであり、ここで `U` は `N*bitsize(T)` ビットを持つ符号なし整数型であり、`BitIntegers` パッケージによって定義されている可能性があります。それ以外の場合、結果は次の符号なし整数型 `U` にゼロ拡張されます。この型のビット長は `2` の累乗です。

要素型が `Bool` の場合、各要素は戻り値で1ビットのみを占めます。もし `N` が `8` 未満または `2` の累乗でない場合、結果は再びゼロ拡張されます。

詳細は [`SmallCollections.bitsize`](@ref)、`Base.BitInteger`、`Base.reinterpret`、`BitIntegers` を参照してください。

# 例

```jldoctest
julia> SmallCollections.FixedVector{4,Int8}(1:4) |> bits
0x04030201

julia> SmallCollections.FixedVector{3}('a':'c') |> bits
0x00000000630000006200000061000000

julia> m = SmallCollections.FixedVector{6,UInt32}(1:6) |> bits
0x0000000000000000000000060000000500000004000000030000000200000001

julia> typeof(m)
BitIntegers.UInt256

julia> SmallCollections.FixedVector{22}(map(isodd, 1:22)) |> bits
0x00155555
```
