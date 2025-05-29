```
@slot(slotname)
```

テンプレートにv-slot属性を追加します。

### 例

```julia
julia> template(@slot(:header), [cell("Header")])
"<template v-slot:header><div class="st-col col">Header</div></template>"
```
