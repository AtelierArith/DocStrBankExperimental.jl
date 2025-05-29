```
nufft1d1!(xj      :: Array{Float64} or Array{Float32}, 
          cj      :: Array{ComplexF64} or Array{ComplexF32}, 
          iflag   :: Integer, 
          eps     :: Real,
          fk      :: Array{ComplexF64} or Array{ComplexF32};
          kwargs...
        )
```

Compute type-1 1D complex nonuniform FFT. Output written to `fk`. See `nufft1d1`.
