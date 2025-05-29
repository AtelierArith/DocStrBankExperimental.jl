```
nufft3d1!(xj      :: Array{Float64} or Array{Float32}, 
          yj      :: Array{Float64} or Array{Float32}, 
          zj      :: Array{Float64} or Array{Float32}, 
          cj      :: Array{ComplexF64} or Array{ComplexF32}, 
          iflag   :: Integer, 
          eps     :: Real,
          fk      :: Array{ComplexF64} or Array{ComplexF32};
          kwargs...
        )
```

Compute type-1 3D complex nonuniform FFT. Output written to `fk`. See `nufft3d1`.
