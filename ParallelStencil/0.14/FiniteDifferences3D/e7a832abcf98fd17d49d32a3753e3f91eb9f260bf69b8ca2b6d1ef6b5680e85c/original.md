Module FiniteDifferences3D

Provides macros for 3-D finite differences computations. The dimensions x, y and z refer to the 1st, 2nd and 3rd array dimensions, respectively. The module was designed to enable a math-close notation and, as a consequence, it does not allow for a nested invocation of the provided macros as, e.g., `@inn_z(@inn_y(@d_xa(A)))` (instead, one can simply write `@d_xi(A)`). Additional macros can be straightforwardly added in the caller module to cover eventual missing functionality. The module is intended for usage with the module ParallelStencil.

# Usage

```
using ParallelStencil.FiniteDifferences3D
```

# Macros

###### Differences

  * [`@d_xa`](@ref)
  * [`@d_ya`](@ref)
  * [`@d_za`](@ref)
  * [`@d_xi`](@ref)
  * [`@d_yi`](@ref)
  * [`@d_zi`](@ref)
  * [`@d2_xi`](@ref)
  * [`@d2_yi`](@ref)
  * [`@d2_zi`](@ref)

###### Selection

  * [`@all`](@ref)
  * [`@inn`](@ref)
  * [`@inn_x`](@ref)
  * [`@inn_y`](@ref)
  * [`@inn_z`](@ref)
  * [`@inn_xy`](@ref)
  * [`@inn_xz`](@ref)
  * [`@inn_yz`](@ref)

###### Averages

  * [`@av`](@ref)
  * [`@av_xa`](@ref)
  * [`@av_ya`](@ref)
  * [`@av_za`](@ref)
  * [`@av_xi`](@ref)
  * [`@av_yi`](@ref)
  * [`@av_zi`](@ref)
  * [`@av_xya`](@ref)
  * [`@av_xza`](@ref)
  * [`@av_yza`](@ref)
  * [`@av_xyi`](@ref)
  * [`@av_xzi`](@ref)
  * [`@av_yzi`](@ref)

###### Harmonic averages

  * [`@harm`](@ref)
  * [`@harm_xa`](@ref)
  * [`@harm_ya`](@ref)
  * [`@harm_za`](@ref)
  * [`@harm_xi`](@ref)
  * [`@harm_yi`](@ref)
  * [`@harm_zi`](@ref)
  * [`@harm_xya`](@ref)
  * [`@harm_xza`](@ref)
  * [`@harm_yza`](@ref)
  * [`@harm_xyi`](@ref)
  * [`@harm_xzi`](@ref)
  * [`@harm_yzi`](@ref)

###### Others

  * [`@maxloc`](@ref)
  * [`@minloc`](@ref)

To see a description of a macro type `?<macroname>` (including the `@`).
