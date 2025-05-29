```
Disk
```

Represents a perturbation disc in the complex plane. `Disk(0.5, 2)` represents all perturbations in the circle centered at 1.25 with radius 0.75, or in other words, a gain margin of 2 and a phase margin of 36.9 degrees.

A disk can be converted to a Nyquist exclusion disk by `nyquist(disk)` and plotted using `plot(disk)`.

# Arguments:

  * `γmin`: Lower intercept
  * `γmax`: Upper intercept
  * `c`: Center
  * `r`: Radius
  * `ϕm`: Angle of tangent line through origin.

If γmax < γmin the disk is inverted. See [`diskmargin`](@ref) for disk margin computations. 
