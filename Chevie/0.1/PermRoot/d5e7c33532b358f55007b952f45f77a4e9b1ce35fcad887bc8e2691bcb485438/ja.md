`reflectionMatrix(r, ζ=-1)`

は、根 `r` と固有値 `ζ` によって決定される単位複素反射の行列を返します。これは、ベクトル空間とその双対がスカラー積 `<x,y>=transpose(x)*conj(y)` を介して同一視されるときのことです。コルート `rᵛ` は、線形形式 `x->(1-ζ)<x,r>/<r,r>` に等しくなります。

```julia-repl
julia> reflectionMatrix([1,0,-E(3,2)])
3×3 Matrix{Cyc{Rational{Int64}}}:
  0  0  ζ₃²
  0  1    0
 ζ₃  0    0
```
