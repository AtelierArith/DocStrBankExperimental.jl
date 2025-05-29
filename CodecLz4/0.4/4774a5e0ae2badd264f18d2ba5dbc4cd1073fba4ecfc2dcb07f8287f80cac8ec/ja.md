```
lz4_decompress(input::Union{Vector{UInt8},Base.CodeUnits{UInt8}}, expected_size::Integer=input.size * 2)
```

`input`をLZ4*decompress*safeを使用して解凍します。`expected_size`は、入力の期待される解凍サイズと等しいかそれ以上でなければならず、そうでない場合は解凍に失敗します。解凍されたデータのVector{UInt8}を返します。
