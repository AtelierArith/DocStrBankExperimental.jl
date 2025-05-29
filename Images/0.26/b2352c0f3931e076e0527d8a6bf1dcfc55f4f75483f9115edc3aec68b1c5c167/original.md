```
grad_y, grad_x, mag, orient = imedge(img, kernelfun=KernelFactors.ando3, border="replicate")
```

Edge-detection filtering. `kernelfun` is a valid kernel function for [`imgradients`](@ref), defaulting to [`KernelFactors.ando3`](@ref). `border` is any of the boundary conditions specified in `padarray`.

Returns a tuple `(grad_y, grad_x, mag, orient)`, which are the horizontal gradient, vertical gradient, and the magnitude and orientation of the strongest edge, respectively.
