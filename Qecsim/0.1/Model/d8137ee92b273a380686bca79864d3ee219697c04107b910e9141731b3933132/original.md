```
validate(code)
```

Perform sanity checks.

If any of the following fail then a [`QecsimError`](@ref) is thrown:

  * $S ⊙ S^T = 0$
  * $S ⊙ L^T = 0$
  * $L ⊙ L^T = Λ$

where $S$ and $L$ are the code [`stabilizers`](@ref) and [`logicals`](@ref), respectively, and $⊙$ and $Λ$ are defined in [`PauliTools.bsp`](@ref bsp).
