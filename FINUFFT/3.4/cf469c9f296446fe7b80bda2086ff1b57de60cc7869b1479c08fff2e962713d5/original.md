```
nufft1d2!(xj      :: Array{Float64} or Array{Float32}, 
          cj      :: Array{ComplexF64} or Array{ComplexF32}, 
          iflag   :: Integer, 
          eps     :: Real,
          fk      :: Array{ComplexF64} or Array{ComplexF32};
          kwargs...
        )
```

Compute type-2 1D complex nonuniform FFT. Output written to `cj`. See `nufft1d2`.
