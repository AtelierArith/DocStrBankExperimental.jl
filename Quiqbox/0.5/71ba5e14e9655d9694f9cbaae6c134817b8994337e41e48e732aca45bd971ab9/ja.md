```
normalizeBasis(b::GTBasisFuncs{T, D, 1}) where {T, D} -> GTBasisFuncs{T, D, 1}
```

`b`の内部の収縮係数を定数係数で掛けて`b`を正規化し、その後正規化された基底を返します。
