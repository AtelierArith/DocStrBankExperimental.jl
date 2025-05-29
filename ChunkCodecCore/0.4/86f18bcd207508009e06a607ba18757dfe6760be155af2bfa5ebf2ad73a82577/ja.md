```
encode(e, src::AbstractVector{UInt8})::Vector{UInt8}
```

エンコーダー `e` を使用して入力ベクター `src` をエンコードします。`e` は [`decoded_size_range`](@ref)、[`encode_bound`](@ref)、および [`try_encode!`](@ref) を実装している必要があります。

`length(src)` が `decoded_size_range(e)` に含まれていない場合はエラーをスローします。

それ以外の場合はエラーをスローします。

詳細は [`EncodeOptions`](@ref) および [`decode`](@ref) を参照してください。
