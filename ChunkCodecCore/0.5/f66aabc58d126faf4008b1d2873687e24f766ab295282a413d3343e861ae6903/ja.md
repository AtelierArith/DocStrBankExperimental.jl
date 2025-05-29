```
try_resize_decode!(d, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}, max_size::Int64; kwargs...)::Union{Nothing, Int64}
```

入力 `src` をデコーダ `d` を使用して `dst` にデコードしようとします。

成功した場合、デコードされた出力のサイズを `dst` に返します。

`dst` は `resize!` 関数を使用して、元の長さの1以上から `max_size` までの任意のサイズに拡張できます。

`dst` のサイズがデコードされた出力を含むには小さすぎて、`max_size` 制限のために拡張できない場合は `nothing` を返します。

前提条件: `dst` と `src` はメモリ内で重複していません。

`dst` のすべてはデコーダによって書き込むことができるか、またはスクラッチスペースとして使用されます。最初に返されたバイト数のみが有効な出力です。
