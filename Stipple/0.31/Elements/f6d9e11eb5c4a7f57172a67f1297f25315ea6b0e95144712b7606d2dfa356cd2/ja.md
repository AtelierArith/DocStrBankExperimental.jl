```
@slot(slotname, varname)
```

テンプレートに変数名を持つ v-slot 属性を追加します。

### 例

```julia
julia> template(@slot(:body, :props), ["{{ props.value }}"])
"<template v-slot:body=\"props\">{{ props.value }}</template>"
```
