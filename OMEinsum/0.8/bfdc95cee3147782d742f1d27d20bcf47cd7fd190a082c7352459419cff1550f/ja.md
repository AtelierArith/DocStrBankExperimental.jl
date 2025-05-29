```
getixsv(code)
```

`EinCode`、`NestedEinsum` およびその他の einsum のようなオブジェクトの入力テンソルのラベルを取得します。ベクトルのベクトルを返します。

```jldoctest; setup = :(using OMEinsum)
julia> getixsv(ein"(ij,jk),k->i")
3-element Vector{Vector{Char}}:
 ['i', 'j']
 ['j', 'k']
 ['k']
```
