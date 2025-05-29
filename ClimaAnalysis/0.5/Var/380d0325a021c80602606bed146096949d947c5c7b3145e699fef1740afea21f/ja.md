```
set_dim_units!(var::OutputVar, dim_name::AbstractString, units::AbstractString)
```

`var`の`dim_name`次元の`units`を設定します。

!!! warning "既存の単位を上書きする"
    次元に既に単位が存在する場合、これは`var`の次元の単位を上書きします。

