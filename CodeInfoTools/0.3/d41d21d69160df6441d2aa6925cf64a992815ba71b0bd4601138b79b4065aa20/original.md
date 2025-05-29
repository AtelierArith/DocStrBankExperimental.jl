```
const Variable = Core.SSAValue
var(id::Int) = Variable(id)
```

Alias for `Core.SSAValue` – represents a primitive register in lowered code. See the section of Julia's documentation on [lowered forms](https://docs.julialang.org/en/v1/devdocs/ast/#Lowered-form) for more information.
