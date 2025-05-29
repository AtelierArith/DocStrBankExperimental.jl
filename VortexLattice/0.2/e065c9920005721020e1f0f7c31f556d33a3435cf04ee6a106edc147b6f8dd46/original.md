```
far_field_drag(receiving, sending, reference, symmetric)
```

Computes the induced drag on `receiving` from `sending` using the Trefftz plane analysis.

# Arguments

  * `receiving`: Vector of receiving Trefftz panels (see [`TrefftzPanel`](@ref))
  * `sending`: Vector of sending Trefftz panels (see [`TrefftzPanel`](@ref))
  * `reference`: Reference parameters (see [`Reference`](@ref))
  * `symmetric`: Flag indicating whether a mirror image of the panels in `surface`,  should be used when calculating induced velocities
