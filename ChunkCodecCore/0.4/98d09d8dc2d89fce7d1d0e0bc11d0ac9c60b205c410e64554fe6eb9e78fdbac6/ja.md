```
try_find_decoded_size(d, src::AbstractVector{UInt8})::Union{Nothing, Int64}
```

`d`を使用して`src`のデコードされた出力のサイズを返そうとします。

サイズを迅速に決定できない場合は、`nothing`を返します。

エンコードされたデータが無効であることが判明した場合は、`DecodingError`をスローします。

`Int64`が返される場合、それはデコードされた出力の正確なサイズでなければなりません。[`try_decode!`](@ref)がこのサイズの`dst`で呼び出されると、成功し、同じサイズを返すか、エラーをスローしなければなりません。
