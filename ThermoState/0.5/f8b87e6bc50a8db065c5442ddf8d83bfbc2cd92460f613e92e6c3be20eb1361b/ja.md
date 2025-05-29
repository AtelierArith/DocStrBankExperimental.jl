```
default_units(::Union{Type{AbstractSpec},Type{property_function}})
```

はスペックのデフォルト単位を返します

# 例

```julia-repl
default_units(pressure) #関数名
Pa

default_units(Gibbs{MOLAR}) #スペックタイプ
J/mol
```
