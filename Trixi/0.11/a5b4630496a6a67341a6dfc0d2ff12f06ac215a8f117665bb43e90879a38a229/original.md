```
BoundsCheckCallback(; output_directory="out", save_errors=false, interval=1)
```

Subcell limiting techniques with [`SubcellLimiterIDP`](@ref) are constructed to adhere certain local or global bounds. To make sure that these bounds are actually met, this callback calculates the maximum deviation from the bounds. The maximum deviation per applied bound is printed to the screen at the end of the simulation. For more insights, when setting `save_errors=true` the occurring errors are exported every `interval` time steps during the simulation. Then, the maximum deviations since the last export are saved in "`output_directory`/deviations.txt". The `BoundsCheckCallback` has to be applied as a stage callback for the SSPRK time integration scheme.

!!! note
    For `SubcellLimiterIDP`, the solution is corrected in the a posteriori correction stage [`SubcellLimiterIDPCorrection`](@ref). So, to check the final solution, this bounds check callback must be called after the correction stage.

