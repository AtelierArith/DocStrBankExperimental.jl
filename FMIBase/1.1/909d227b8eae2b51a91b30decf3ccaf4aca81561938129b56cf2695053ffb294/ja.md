```
stringToValueReference(obj, names)
```

指定された `name` の値参照を見つけます。

# 引数

  * `obj ∈ (fmi2ModelDescription, fmi3ModelDescription, FMU2, FMU3)` FMIオブジェクト
  * `names ∈ (String, AbstractVector{String})` 値参照名または複数の名前

# 戻り値

変数名に対応する単一または配列の `fmi2ValueReferences` (FMI2) または `fmi3ValueReferences` (FMI3) を返します。
