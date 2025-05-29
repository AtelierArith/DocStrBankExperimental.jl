```
StringView{T<:AbstractVector{UInt8}} <: AbstractString
```

`StringView(array)` は、UTF-8 エンコードされた Unicode として解釈される任意の `UInt8` データの `array` の `AbstractString` 表現を作成します。これは `array` のコピーを作成したり、変更したりすることはありません。

`StringView(buf::IOBuffer)` は、`buf` の現在の内容の文字列ビューを返し、`String(take!(buf))` と同等ですが、コピーを作成しません。 `StringView(buf::IOBuffer, range)` は、バッファ内のバイト `range` のビューです（デフォルトは `1:position(buf)-1` です）。
