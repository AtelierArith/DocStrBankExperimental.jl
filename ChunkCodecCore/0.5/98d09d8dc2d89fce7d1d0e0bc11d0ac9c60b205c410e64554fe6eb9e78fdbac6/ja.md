```
try_find_decoded_size(d, src::AbstractVector{UInt8})::Union{Nothing, Int64}
```

`src`のデコードされた出力のサイズを`d`を使用して返そうとします。

サイズを迅速に決定できない場合は、`nothing`を返します。

エンコードされたデータが無効であることが判明した場合は、`DecodingError`をスローします。

`Int64`が返される場合、それはデコードされた出力の正確なサイズでなければなりません。もし[`try_decode!`](@ref)がこのサイズの`dst`で呼び出されると、成功し、同じサイズを返すか、エラーをスローしなければなりません。
