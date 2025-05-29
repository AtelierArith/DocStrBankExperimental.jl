```
nufft1d2!(xj      :: Array{Float64} or Array{Float32}, 
          cj      :: Array{ComplexF64} or Array{ComplexF32}, 
          iflag   :: Integer, 
          eps     :: Real,
          fk      :: Array{ComplexF64} or Array{ComplexF32};
          kwargs...
        )
```

タイプ2の1D複素非一様FFTを計算します。出力は`cj`に書き込まれます。`nufft1d2`を参照してください。
