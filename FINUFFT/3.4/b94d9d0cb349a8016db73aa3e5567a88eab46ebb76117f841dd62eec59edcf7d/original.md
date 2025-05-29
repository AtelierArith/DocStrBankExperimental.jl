```
nufft3d3!(xj      :: Array{Float64} or Array{Float32}, 
          yj      :: Array{Float64} or Array{Float32},
          zj      :: Array{Float64} or Array{Float32},
          cj      :: Array{ComplexF64} or Array{ComplexF32}, 
          iflag   :: Integer, 
          eps     :: Real,
          sk      :: Array{Float64} or Array{Float32},
          tk      :: Array{Float64} or Array{Float32},
          uk      :: Array{Float64} or Array{Float32},
          fk      :: Array{ComplexF64} or Array{ComplexF32};
          kwargs...
         )
```

Compute type-3 3D complex nonuniform FFT. Output written to `fk`. See `nufft3d3`.
