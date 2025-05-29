Module FiniteDifferences1D

Provides macros for 1-D finite differences computations. The dimensions x refers to the 1st and only array dimension. The module was designed to enable a math-close notation and, as a consequence, it does not allow for a nested invocation of the provided macros as, e.g., `@d(@d(A))` (instead, one can simply write `@d2(A)`). Additional macros can be straightforwardly added in the caller module to cover eventual missing functionality. The module is intended for usage with the module ParallelStencil.

# Usage

```
using ParallelStencil.FiniteDifferences1D
```

# Macros

###### Differences

  * [`@d`](@ref)
  * [`@d2`](@ref)

###### Selection

  * [`@all`](@ref)
  * [`@inn`](@ref)

###### Averages

  * [`@av`](@ref)

###### Harmonic averages

  * [`@harm`](@ref)

###### Others

  * [`@maxloc`](@ref)
  * [`@minloc`](@ref)

To see a description of a macro type `?<macroname>` (including the `@`).
