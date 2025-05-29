```
@data(expr)
```

Creates a Vue.js data binding for the elements that expect it.

### Example

```julia
julia> plot(@data(:piechart), options! = "plot_options")
"<template><apexchart :options="plot_options" :series="piechart"></apexchart></template>"
```
