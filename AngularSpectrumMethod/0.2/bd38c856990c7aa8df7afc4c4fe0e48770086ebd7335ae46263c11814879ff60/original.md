```
ASM(u, λ, Δx, Δy, z; expand=true)
```

return diffracted field by the angular spectrum method (ASM). Evanescent waves are not eliminated but attenuated as $\exp(-2{\pi}wz)$. Without attenuation, the total energy $\iint|u|\mathrm{d}x\mathrm{d}y$ is conserved.

# Arguments

  * `u`: input field.
  * `λ`: wavelength.
  * `Δx`: sampling interval the in x-axis.
  * `Δy`: sampling interval the in y-axis.
  * `z`: diffraction distance.
  * `expand=true`: if true (default), perform 4× expansion and zero padding for aliasing suppression.

!!! note
    The x-axis is the horizontal direction, and the y-axis is the vertical.

