```
fbp(plan, sino)
```

Filtered back-projection (FBP) reconstruction.

# in

  * `plan::FBPplan`
  * `sino::AbstractArray{<:Number} (nb,na,...)` sinogram(s)

# out

  * `image::Matrix{<:Number} (nx,ny,...)` reconstructed image(s)
