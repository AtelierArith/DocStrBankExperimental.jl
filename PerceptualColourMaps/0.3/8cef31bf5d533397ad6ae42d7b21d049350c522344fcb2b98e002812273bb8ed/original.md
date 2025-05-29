relief -  Generates relief shaded image

```
Usage:  shadeimg = relief(img, azimuth, elevation, gradscale, rgbimg)

Arguments: img - Image/heightmap to be relief shaded. ::Array{T<:Real,2}
       azimuth - Of light direction in degrees. Zero azimuth points
                 upwards and increases clockwise. Defaults to 45.
     elevation - Of light direction in degrees. Defaults to 45.
     gradscale - Scaling to apply to the surface gradients.  If the shading
                 is excessive decrease the scaling. Try successive doubling
                 or halving to find a good value.
        rgbimg - Optional RGB image to which the shading pattern derived
                 from 'img' is applied.   Alternatively, rgbimg can be a
                 colour map of type ::Array{ColorTypes.RGBA{Float64},1}
                 obtained from cmap().  This colour map is applied to the input
                 image/heightmap in order to obtain a RGB image to which
                 the shading pattern is applied.
```

Lambertian shading is used to form the relief image.  This obtained from the cosine of the angle between the surface normal and light direction.  Note that shadows are ignored.  Thus a small feature that might otherwise be in the shadow of a nearby large structure is rendered as if the large feature was not there.

See also: cmap, applycolourmap
