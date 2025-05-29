```
getinterp(b::Basis)
```

与えられた [`Basis`](@ref) の補間行列を取得します。与えられた $H^1$ 基底の場合はサイズ `(getnumqpts(b), getnumnodes(b))` の行列を返し、与えられたベクトル $H(div)$ または $H(curl)$ 基底の場合はサイズ `(getdimension(b), getnumqpts(b), getnumnodes(b))` の行列を返します。
