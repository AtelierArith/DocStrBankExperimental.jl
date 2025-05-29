```
getinterp1d(b::Basis)
```

与えられた [`Basis`](@ref) の 1D 補間行列を取得します。`b` はテンソル積基底でなければならず、そうでない場合はこの関数は失敗します。サイズ `(getnumqpts1d(b), getnumnodes1d(b))` の行列を返します。
