```
nufft2d2!(xj      :: Array{Float64} or Array{Float32}, 
          yj      :: Array{Float64} or Array{Float32}, 
          cj      :: Array{ComplexF64} or Array{ComplexF32}, 
          iflag   :: Integer, 
          eps     :: Real,
          fk      :: Array{ComplexF64} or Array{ComplexF32};
          kwargs...
        )
```

Compute type-2 2D complex nonuniform FFT. Output written to `cj`. See `nufft2d2`.
