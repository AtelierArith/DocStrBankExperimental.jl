```
@slot(slotname, varname)
```

Add a v-slot attribute with a variable name to a template.

### Example

```julia
julia> template(@slot(:body, :props), ["{{ props.value }}"])
"<template v-slot:body="props">{{ props.value }}</template>"
```
