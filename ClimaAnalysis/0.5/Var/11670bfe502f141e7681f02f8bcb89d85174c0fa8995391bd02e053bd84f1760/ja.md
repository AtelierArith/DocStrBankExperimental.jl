```
Var.convert_dim_units(var, dim_name, new_units; conversion_function = nothing)
```

`dim_name`の物理単位を`new_units`に変換した新しいOutputVarを返します。`conversion_function`を使用します。

この関数はUnitfulをサポートしていないため、`conversion_function`パラメータを指定する必要があります。
