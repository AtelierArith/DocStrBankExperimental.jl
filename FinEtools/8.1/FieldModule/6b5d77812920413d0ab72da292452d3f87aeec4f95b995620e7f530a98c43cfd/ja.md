```
gathersysvec(self::F, kind::KIND_INT = DOF_KIND_FREE) where {F<:AbstractField}
```

フィールドからシステムベクトルの値を収集します。

# 引数

  * `self`: フィールド;
  * `kind`: 収集する自由度の種類; デフォルトは `DOF_KIND_FREE` です。
