```
getgrad(b::Basis)
```

与えられた [`Basis`](@ref) の勾配行列を取得します。サイズ `(getdimension(b), getnumqpts(b), getnumnodes(b))` のテンソルを返します。
