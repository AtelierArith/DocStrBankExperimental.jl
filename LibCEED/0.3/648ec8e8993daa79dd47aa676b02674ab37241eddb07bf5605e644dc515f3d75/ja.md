```
getgrad1d(b::Basis)
```

与えられた [`Basis`](@ref) の 1D 導関数行列を取得します。サイズは `(getnumqpts(b), getnumnodes(b))` の行列を返します。
