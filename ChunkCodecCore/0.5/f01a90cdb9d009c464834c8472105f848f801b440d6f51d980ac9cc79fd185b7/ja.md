```
encode_bound(e, src_size::Int64)::Int64
```

`src`の内容に関係なく[`try_encode!`](@ref)が成功することを保証するために必要な`dst`のサイズを返します。`src_size`が[`decoded_size_range(e)`](@ref)に含まれ、十分なメモリがある場合に限ります。

`0:typemax(Int64)`の範囲内で、この関数はエラーを返さず、単調増加でなければなりません。
