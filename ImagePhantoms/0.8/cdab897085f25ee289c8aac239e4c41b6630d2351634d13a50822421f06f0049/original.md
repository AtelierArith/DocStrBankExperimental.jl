```
spectrum(oa::Array{<:Object3d})::Function
```

Return function `kspace(fx,fy,fz)` that user can sample at any spatial frequency locations to evaluate the spectrum (3D Fourier transform) for an `Array` of 3D objects.
