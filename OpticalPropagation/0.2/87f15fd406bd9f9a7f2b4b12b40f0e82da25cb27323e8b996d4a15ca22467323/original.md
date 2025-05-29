```
fresnel2(Uin, d, λ, lx, ly)
```

calculate the propagation light field based on the Fresnel diffraction with double Fourier transform.

## Arguments

  * `Uin::AbstractArray{<:Number,2}`: Complex array of input complex amplitude.
  * `d::Real`: Distance to propagate in metres.
  * `λ::Real`: Wavelength of light to propagate.
  * `lx::Real`: The physical size of the input data along the x-axis.
  * `ly::Real`: The physical size of the input data along the y-axis.

## Returns

  * `::Array{<:Number,2}`: Complex amplitude data after propagation.
