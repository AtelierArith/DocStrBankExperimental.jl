```
@data(expr)
```

Vue.jsのデータバインディングを、期待される要素のために作成します。

### 例

```julia
julia> plot(@data(:piechart), options! = "plot_options")
"<template><apexchart :options="plot_options" :series="piechart"></apexchart></template>"
```
