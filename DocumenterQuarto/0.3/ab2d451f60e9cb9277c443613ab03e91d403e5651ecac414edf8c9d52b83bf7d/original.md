```julia
autodoc(mod, symbols; delimiter)

```

Automatically process and return documentation for symbols in the provided  module. If no symbols are provided, all exported symbols are used. The  `delimiter` keyword argument is printed in between each documented name.

## Example

```julia
import LinearAlgebra
DocumenterQuarto.autodoc(LinearAlgebra)
```
