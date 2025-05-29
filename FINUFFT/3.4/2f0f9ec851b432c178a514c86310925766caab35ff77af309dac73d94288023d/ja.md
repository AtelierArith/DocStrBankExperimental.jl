```
nufft2d1!(xj      :: Array{Float64} or Array{Float32}, 
          yj      :: Array{Float64} or Array{Float32}, 
          cj      :: Array{ComplexF64} or Array{ComplexF32}, 
          iflag   :: Integer, 
          eps     :: Real,
          fk      :: Array{ComplexF64} or Array{ComplexF32};
          kwargs...
        )
```

タイプ1の2D複素非一様FFTを計算します。出力は`fk`に書き込まれます。`nufft2d1`を参照してください。
