```
Subpixel(ap, N=1) <: AbstractAperture
```

Use a subpixel quadrature approximation for pixel shading instead of exact geometric methods.

For any pixel laying on the border of `ap`, this alters the shading algorithm by breaking the border pixel up into `(N, N)` subpixels. The shading value is the fraction of these subpixels within the geometric border of `ap`.

Using a subpixel shading method is sometimes faster than exact methods at the cost of accuracy. For [`CircularAperture`](@ref) the subpixel method is only faster than the exact method for `N` ~ 7. for [`EllipticalAperture`](@ref) the cutoff is `N` ~ 12, and for [`RectangularAperture`](@ref) the cutoff is `N` ~ 20.

# Examples

```jldoctest
julia> ap = CircularAperture(3, 3, 2.5)
5×5 CircularAperture{Float64} with indices 1:5×1:5:
 0.136857  0.769325  0.983232  0.769325  0.136857
 0.769325  1.0       1.0       1.0       0.769325
 0.983232  1.0       1.0       1.0       0.983232
 0.769325  1.0       1.0       1.0       0.769325
 0.136857  0.769325  0.983232  0.769325  0.136857

julia> sub_ap = Subpixel(ap, 5)
5×5 Subpixel{Float64, CircularAperture{Float64}} with indices 1:5×1:5:
 0.12  0.76  1.0  0.76  0.12
 0.76  1.0   1.0  1.0   0.76
 1.0   1.0   1.0  1.0   1.0
 0.76  1.0   1.0  1.0   0.76
 0.12  0.76  1.0  0.76  0.12
```

!!! note
    `photutils` offers a `center` shading method which is equivalent to using the `Subpixel` method with 1 subpixel. To avoid unneccessary namespace cluttering, we simply instruct users to use `Subpixel(ap)` instead.

