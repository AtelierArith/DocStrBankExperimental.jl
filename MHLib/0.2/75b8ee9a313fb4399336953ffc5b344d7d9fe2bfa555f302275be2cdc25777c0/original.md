```
GVNS{TSolution <: Solution(solution, meths_ch, meths_li, meths_sh, 
    consider_initial_sol=false)
```

Create a GVNS.

Create a GVNS for the given solution with the given construction, local improvement, and shaking methods provides as `Vector{MHMethod}`. If `consider_initial_sol` is true, consider the given solution as valid initial solution; otherwise it is assumed to be uninitialized.
