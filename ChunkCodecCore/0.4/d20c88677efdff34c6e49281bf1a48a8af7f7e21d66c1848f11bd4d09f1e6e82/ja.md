```
try_resize_decode!(d, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}, max_size::Int64; kwargs...)::Union{Nothing, Int64}
```

デコーダ `d` を使用して、入力 `src` を `dst` にデコードしようとします。

成功した場合、デコードされた出力のサイズを `dst` に返します。

`dst` が小さすぎる場合、`dst` をリサイズして再試行します。`max_size` 制限を超える場合は、`nothing` を返します。

`dst` は、元の長さと `max_size` の間の任意のサイズに `resize!` 関数を使用してリサイズできます。

`length(dst)` が `0:max_size` にない場合は、`ArgumentError` をスローします。

前提条件: `dst` と `src` はメモリ内で重複していません。

デコーダによって、`dst` のすべての部分に書き込むことができるか、またはスクラッチスペースとして使用されます。最初に返されたバイト数のみが有効な出力です。

`dst` のサイズが増加した場合、その長さは返されたバイト数に等しくなります。
