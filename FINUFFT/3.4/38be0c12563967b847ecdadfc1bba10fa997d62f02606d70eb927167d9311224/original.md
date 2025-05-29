```
nufft1d3!(xj      :: Array{Float64} or Array{Float32}, 
          cj      :: Array{ComplexF64} or Array{ComplexF32}, 
          iflag   :: Integer, 
          eps     :: Real,
          sk      :: Array{Float64} or Array{Float32},
          fk      :: Array{ComplexF64} or Array{ComplexF32};
          kwargs...
         )
```

Compute type-3 1D complex nonuniform FFT. Output written to `fk`. See `nufft1d3`.
