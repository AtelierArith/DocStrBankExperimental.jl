```
apply_t_cumul_grad!(climate_2D_step::Climate2Dstep, S::Matrix{F}) where {F <: AbstractFloat}
```

Apply temperature and precipitation gradients based on the positive degree day (PDD) and on the elevation matrix `S` to the climate data in `climate_2D_step`.

# Arguments

  * `climate_2D_step::Climate2Dstep`: The climate data structure containing temperature, PDD, gradients, and reference height.
  * `S::Matrix{F}`: A matrix of elevations.

# Description

This function updates the temperature and PDD fields in `climate_2D_step` by applying the respective gradients based on the difference between the elevation matrix `S` and the reference height. Negative PDD values are cropped to zero. Additionally, the function adjusts the rain and snow fractions based on the updated temperature values.
