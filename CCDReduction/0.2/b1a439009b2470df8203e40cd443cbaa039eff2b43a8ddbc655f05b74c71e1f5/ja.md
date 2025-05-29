```
combine(frames...; method = median, [hdu = 1], [header_hdu = 1])
combine(frames; method = median, [hdu = 1], [header_hdu = 1])
```

複数のフレームを `method` を使用して結合します。複数のフレームは、ベクトルまたは生成器として渡すこともできます。

カスタムメソッドを渡す場合、そのシグネチャは `method(::AbstractArray; dims)` のようでなければなりません。

`frames` が文字列の場合、最初に [`CCDData`](@ref) に読み込まれます。HDU インデックスは、各ファイルに対応する整数またはタプルとして `hdu` で指定できます。

出力ファイルのヘッダー（該当する場合）は、デフォルトで 1 の `header_hdu` によって指定されます。

# 例

```jldoctest
julia> frame = [reshape(1.0:4.0, (2, 2)) for i = 1:4];

julia> combine(frame)
2×2 Matrix{Float64}:
 1.0  3.0
 2.0  4.0

julia> combine(frame, method = sum)
2×2 Matrix{Float64}:
 4.0  12.0
 8.0  16.0

```
