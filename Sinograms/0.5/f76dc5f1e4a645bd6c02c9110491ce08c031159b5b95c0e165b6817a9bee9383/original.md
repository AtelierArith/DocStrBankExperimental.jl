```
img = fbp_back(rg, ig, sino ; ia_skip)
```

2D pixel-driven backprojection for FBP.

# in

  * `rg::SinoGeom`
  * `ig::ImageGeom`
  * `sino::AbstractArray{<:Number}` sinogram(s) (line integrals), usually ramp filtered

# option

  * `ia_skip::Int` downsample in angle to save time for quick tests (default: 1)

# out

  * `img::Array{<:Number}` reconstructed image(s)
