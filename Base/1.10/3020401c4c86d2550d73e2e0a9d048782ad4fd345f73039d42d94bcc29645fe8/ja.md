```
cat(A...; dims)
```

指定された次元 `dims` に沿って入力配列を連結します。

次元 `d in dims` に沿って、出力配列のサイズは `sum(size(a,d) for a in A)` です。他の次元に沿っては、すべての入力配列が同じサイズである必要があり、それが出力配列のサイズにもなります。

`dims` が単一の数値の場合、異なる配列はその次元に沿って密に詰められます。`dims` が複数の次元を含むイテラブルの場合、これらの次元に沿った位置は各入力配列に対して同時に増加し、他の場所はゼロで埋められます。これにより、`cat(matrices...; dims=(1,2))` のようにブロック対角行列やその高次元の類似物を構築することができます。

特別なケース `dims=1` は [`vcat`](@ref) であり、`dims=2` は [`hcat`](@ref) です。さらに [`hvcat`](@ref)、[`hvncat`](@ref)、[`stack`](@ref)、[`repeat`](@ref) も参照してください。

キーワードは `Val(dims)` も受け入れます。

!!! compat "Julia 1.8"
    複数の次元 `dims = Val(::Tuple)` は Julia 1.8 で追加されました。


# 例

```jldoctest
julia> cat([1 2; 3 4], [pi, pi], fill(10, 2,3,1); dims=2)  # hcat と同じ
2×6×1 Array{Float64, 3}:
[:, :, 1] =
 1.0  2.0  3.14159  10.0  10.0  10.0
 3.0  4.0  3.14159  10.0  10.0  10.0

julia> cat(true, trues(2,2), trues(4)', dims=(1,2))  # ブロック対角
4×7 Matrix{Bool}:
 1  0  0  0  0  0  0
 0  1  1  0  0  0  0
 0  1  1  0  0  0  0
 0  0  0  1  1  1  1

julia> cat(1, [2], [3;;]; dims=Val(2))
1×3 Matrix{Int64}:
 1  2  3
```
