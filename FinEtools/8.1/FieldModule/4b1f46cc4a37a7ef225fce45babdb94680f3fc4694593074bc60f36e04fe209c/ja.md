```
gathersysvec!(self::F, vec::Vector{T}, kind::KIND_INT = DOF_KIND_FREE) where {F<:AbstractField,T}
```

フィールドからシステムベクトルの値を収集します。

# 引数

  * `self`: フィールド;
  * `vec`: 宛先バッファ;
  * `kind`: 整数、収集する自由度の種類: デフォルトは `DOF_KIND_FREE` です。
