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

タイプ3の1D複素非一様FFTを計算します。出力は`fk`に書き込まれます。`nufft1d3`を参照してください。
