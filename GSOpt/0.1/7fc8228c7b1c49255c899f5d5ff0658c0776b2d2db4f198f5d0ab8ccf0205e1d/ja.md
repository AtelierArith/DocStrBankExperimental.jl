```
JuMP.dual(cref::GPConstraintRef) -> Float64
```

制約の双対値（感度）を返します。

# 引数

  * `cref::GPConstraintRef`: 制約の参照

# 返り値

  * 制約の双対値

# 例外

  * モデルがまだ解決されていない場合や双対値が利用できない場合にエラーをスローします。
