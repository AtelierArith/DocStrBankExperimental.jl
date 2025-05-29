```
@slot(slotname)
```

Add a v-slot attribute to a template.

### Example

```julia
julia> template(@slot(:header), [cell("Header")])
"<template v-slot:header><div class="st-col col">Header</div></template>"
```
