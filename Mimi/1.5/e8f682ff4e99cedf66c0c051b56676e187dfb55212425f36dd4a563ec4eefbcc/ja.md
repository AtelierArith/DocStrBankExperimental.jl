```
set_dimension!(m::Model, name::Symbol, keys::Union{Vector, Tuple, AbstractRange})
```

`m`の次元`name`の値を整数1から`count`に設定します。`keys`が整数の場合はそのように設定し、`keys`がベクターまたは範囲のいずれかのタイプである場合は、それらの値に設定します。
