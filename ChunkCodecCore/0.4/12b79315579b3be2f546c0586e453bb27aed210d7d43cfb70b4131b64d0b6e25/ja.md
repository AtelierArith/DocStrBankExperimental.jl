```
decode(d, src::AbstractVector{UInt8}; max_size::Integer=typemax(Int64), size_hint::Integer=Int64(0))::Vector{UInt8}
```

デコーダー `d` を使用して入力データ `src` をデコードします。 `d` は [`try_find_decoded_size`](@ref)、[`try_decode!`](@ref)、およびオプションで [`try_resize_decode!`](@ref) を実装している必要があります。

出力サイズが `max_size` を超えるためにデコードに失敗した場合は、[`DecodedSizeError`](@ref) をスローします。

入力データが無効であるためにデコードに失敗した場合は、[`DecodingError`](@ref) をスローします。

それ以外の場合はエラーをスローします。

デコードサイズの良い見積もりがある場合は、`size_hint` キーワード引数を使用することでパフォーマンスが大幅に向上する可能性があります。

また、[`DecodeOptions`](@ref) と [`encode`](@ref) も参照してください。
