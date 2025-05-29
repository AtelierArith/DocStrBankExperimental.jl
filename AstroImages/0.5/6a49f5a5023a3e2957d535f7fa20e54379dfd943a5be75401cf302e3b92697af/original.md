```
recenter(img::AstroImage)
recenter(img::AstroImage, newcentx, newcenty, ...)
```

Adjust the dimensions of an AstroImage so that they are centered on the pixel locations given by `newcentx`, .. etc. This does not affect the underlying array, it just updates the dimensions associated with it by the AstroImage. If no `newcent` arguments are provided, center the image in all dimensions to the middle pixel (or fractional pixel).

Example:

```julia
a = AstroImage(randn(11,11))
a[1,1] # Bottom left
a[At(1),At(1)] # Bottom left
r = recenter(a, 6, 6)
r[1,1] # Still bottom left
r[At(1),At(1)] # Center pixel
```
