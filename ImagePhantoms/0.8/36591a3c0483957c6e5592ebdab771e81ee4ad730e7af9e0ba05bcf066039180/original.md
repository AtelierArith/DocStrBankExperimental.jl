```
spectrum(oa::Array{<:Object2d})::Function
```

Return function `kspace(fx,fy)` that user can sample at any spatial frequency locations to evaluate the spectrum (2D Fourier transform) for an `Array` of 2D objects.
