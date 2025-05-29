```
try_encode!(e, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}; kwargs...)::Union{Nothing, Int64}
```

エンコーダ `e` を使用して `src` を `dst` にエンコードしようとします。

成功した場合、`dst` にエンコードされた出力のサイズを返します。

`dst` が小さすぎる場合は、`nothing` を返します。

`length(src)` が `decoded_size_range(e)` に含まれていない場合はエラーをスローします。

それ以外の場合はエラーをスローします。

前提条件: `dst` と `src` はメモリ内で重複していません。

`dst` のすべては、エンコーダによって書き込まれるか、スクラッチスペースとして使用されることができます。最初に返されたバイト数のみが有効な出力です。

[`encode_bound`](@ref) および [`decoded_size_range`](@ref) も参照してください。
