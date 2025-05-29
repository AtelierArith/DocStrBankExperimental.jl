```
centered(A, cp=center(A)) -> Ao
```

配列 `A` の中心座標/点 `cp` を `(0, 0, ..., 0)` にシフトします。内部的には、これは `OffsetArray(A, .-cp)` と同等です。

!!! compat "OffsetArrays 1.9"
    このメソッドは少なくとも OffsetArrays 1.9 を必要とします。


# 例

```jldoctest; setup=:(using OffsetArrays)
julia> A = reshape(collect(1:9), 3, 3)
3×3 Matrix{Int64}:
 1  4  7
 2  5  8
 3  6  9

julia> Ao = OffsetArrays.centered(A); # 軸 (-1:1, -1:1)

julia> Ao[0, 0]
5

julia> Ao = OffsetArray(A, OffsetArrays.Origin(0)); # 軸 (0:2, 0:2)

julia> Aoo = OffsetArrays.centered(Ao); # 軸 (-1:1, -1:1)

julia> Aoo[0, 0]
5
```

ユーザーは `cp` を渡して「中心点」の解釈を変更することができますが、出力配列の意味も再解釈する必要があります。たとえば、`cp = map(last, axes(A))` の場合、この関数はもはや中心点をシフトするのではなく、右下の点を `(0, 0, ..., 0)` にシフトします。`cp` の一般的な使用法は、配列がある次元で偶数サイズのときに丸め動作を変更することです：

```jldoctest; setup=:(using OffsetArrays)
julia> A = reshape(collect(1:4), 2, 2) # 理想的には中心は (1.5, 1.5) であるべきですが、OffsetArrays は整数オフセットのみをサポートします
2×2 Matrix{Int64}:
 1  3
 2  4

julia> OffsetArrays.centered(A, OffsetArrays.center(A, RoundUp)) # (2, 2) を中心点として設定
2×2 OffsetArray(::Matrix{Int64}, -1:0, -1:0) with eltype Int64 with indices -1:0×-1:0:
 1  3
 2  4

julia> OffsetArrays.centered(A, OffsetArrays.center(A, RoundDown)) # (1, 1) を中心点として設定
2×2 OffsetArray(::Matrix{Int64}, 0:1, 0:1) with eltype Int64 with indices 0:1×0:1:
 1  3
 2  4
```

詳細は [`center`](@ref OffsetArrays.center) を参照してください。
