```
FixedValueArray{T, N} <: AbstractArray{T, N}
```

すべての要素に対して型 `T` の共通値を持つ、暗黙的かつ任意のサイズの配列。

# コンストラクタ

```
FixedValueArray(val, dims)
FixedValueArray(val, dims...)
```

与えられた次元 `dims` の新しい行列を作成し、各要素は与えられた値 `val` で表されます。

# 例

```jldoctest; setup = :(using ImplicitArrays)
julia> FixedValueArray(0, (2, 5))
2×5 FixedValueArray{Int64, 2}:
 0  0  0  0  0
 0  0  0  0  0

julia> FixedValueArray("(^_^) Hi!", 1, 2)
1×2 FixedValueArray{String, 2}:
 "(^_^) Hi!"  "(^_^) Hi!"

julia> FixedValueArray(FixedValueArray(5.0, (1, 2)), (1, 3))
1×3 FixedValueArray{FixedValueArray{Float64, 2}, 2}:
 [5.0 5.0]  [5.0 5.0]  [5.0 5.0]

julia> length(FixedValueArray(1, 1_000_000_000, 1_000_000_000))
1000000000000000000
```
