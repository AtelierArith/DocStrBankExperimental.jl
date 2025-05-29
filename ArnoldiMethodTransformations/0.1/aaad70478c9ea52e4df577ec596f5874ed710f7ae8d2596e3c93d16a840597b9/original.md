```
module ArnoldiMethodTransformations
```

Provides convenience wrapper for interfacing with the package ArnoldiMethod.

Implements the shift-and-invert transformation detailed [here](https://haampie.github.io/ArnoldiMethod.jl/stable/).

The main functions are `partialschur(A,[B],σ; kwargs...)` and `partialeigen(A,σ; kwargs...)`

The constants `USOLVER`, `PSOLVER`, and `MSOLVER` are exported.
