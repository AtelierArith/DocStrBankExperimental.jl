```
set_dimension!(ccd::CompositeComponentDef, name::Symbol, keys::Union{Int, Vector, Tuple, AbstractRange})
```

`ccd`の次元`name`の値を、`keys`が整数の場合は1から`count`までの整数に設定します。`keys`がベクターまたは範囲のいずれかのタイプである場合は、それらの値に設定します。
