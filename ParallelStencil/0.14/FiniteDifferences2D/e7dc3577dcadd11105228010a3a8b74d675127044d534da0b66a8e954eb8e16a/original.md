Module FiniteDifferences2D

Provides macros for 2-D finite differences computations. The dimensions x and y refer to the 1st and 2nd array dimensions, respectively. The module was designed to enable a math-close notation and, as a consequence, it does not allow for a nested invocation of the provided macros as, e.g., `@inn_y(@d_xa(A))` (instead, one can simply write `@d_xi(A)`). Additional macros can be straightforwardly added in the caller module to cover eventual missing functionality. The module is intended for usage with the module ParallelStencil.

# Usage

```
using ParallelStencil.FiniteDifferences2D
```

# Macros

###### Differences

  * [`@d_xa`](@ref)
  * [`@d_ya`](@ref)
  * [`@d_xi`](@ref)
  * [`@d_yi`](@ref)
  * [`@d2_xa`](@ref)
  * [`@d2_ya`](@ref)
  * [`@d2_xi`](@ref)
  * [`@d2_yi`](@ref)

###### Selection

  * [`@all`](@ref)
  * [`@inn`](@ref)
  * [`@inn_x`](@ref)
  * [`@inn_y`](@ref)

###### Averages

  * [`@av`](@ref)
  * [`@av_xa`](@ref)
  * [`@av_ya`](@ref)
  * [`@av_xi`](@ref)
  * [`@av_yi`](@ref)

###### Harmonic averages

  * [`@harm`](@ref)
  * [`@harm_xa`](@ref)
  * [`@harm_ya`](@ref)
  * [`@harm_xi`](@ref)
  * [`@harm_yi`](@ref)

###### Others

  * [`@maxloc`](@ref)
  * [`@minloc`](@ref)

To see a description of a macro type `?<macroname>` (including the `@`).
