```
StackView(slices...; [dims])
StackView(slices, [dims])
StackView{T}(args...; kwargs...)
```

配列のリスト `slices` を次元 `dims` に沿ってスタック/連結し、データをコピーせずに行います。

指定されていない場合、`dims` は `ndims(first(slices))+1` と定義されます。つまり、末尾に新しい次元が追加されます。これは、メモリレイアウトが列優先の通常のJulia配列に対してより効果的です。

# 例

`StackView` は `cat` とその `vcat`/`hcat`/`hvcat` バリアントに非常に似ています。

```jldoctest; setup=:(using StackViews)
julia> A = reshape(collect(1:6), 2, 3);

julia> B = reshape(collect(7:12), 2, 3);

julia> StackView(A, B, dims=3) # ほぼ `cat(A, B, dims=3)` と同等
2×3×2 StackView{Int64, 3, 3, Tuple{Matrix{Int64}, Matrix{Int64}}}:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12
```

`dim <= ndims(first(slices))` の場合、つまりこの例では `dim <= 2` の場合に違いが生じます。`StackView` は常に新しい次元を作成しますが、`cat` はそうではありません。

```jldoctest; setup=:(using StackViews; A = reshape(collect(1:6), 2, 3); B = reshape(collect(7:12), 2, 3);)
julia> StackView(A, B, dims=1) # `cat(A, B, dims=1)` は 4×3 行列を出力
2×2×3 StackView{Int64, 3, 1, Tuple{Matrix{Int64}, Matrix{Int64}}}:
[:, :, 1] =
 1  2
 7  8

[:, :, 2] =
 3   4
 9  10

[:, :, 3] =
  5   6
 11  12

julia> StackView(A, B, dims=2) # `cat(A, B, dims=2)` は 2×6 行列を出力
2×2×3 StackView{Int64, 3, 2, Tuple{Matrix{Int64}, Matrix{Int64}}}:
[:, :, 1] =
 1  7
 2  8

[:, :, 2] =
 3   9
 4  10

[:, :, 3] =
 5  11
 6  12
```

!!! tip
    型の安定性のために、`Val` を次元として渡すことができます。例えば、`StackView(slices, Val(3))` のようにします。

