Constant b-splines are *nearest-neighbor* interpolations, and effectively return `A[round(Int,x)]` when interpolating without scaling. Scaling can lead to inaccurate position of the *neighbors* due to limited numerical precision.

`Constant{Previous}` interpolates to the previous value and is thus equivalent to `A[floor(Int,x)]` without scaling. `Constant{Next}` interpolates to the next value and is thus equivalent to `A[ceil(Int,x)]` without scaling.
