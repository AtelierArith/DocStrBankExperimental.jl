```
getiy(code)
```

`EinCode`、`NestedEinsum` およびその他の einsum のようなオブジェクトの出力テンソルのラベルを取得します。ベクトルを返します。

```jldoctest; setup = :(using OMEinsum)
julia> getiyv(ein"(ij,jk),k->i")
1-element Vector{Char}:
 'i': ASCII/Unicode U+0069 (category Ll: Letter, lowercase)
```
