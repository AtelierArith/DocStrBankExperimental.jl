```
finufft_exec!(plan::finufft_plan{T},
              input::FINUFFT.InputArray{Complex{T}},
              output::FINUFFT.InputArray{Complex{T}}) where T <: finufftReal
```

計画内で単一または多ベクトルのFINUFFT変換を実行し、出力は事前に割り当てられた配列に書き込まれます。引数については`finufft_exec`を参照してください。

`input`と`output`は連続した配列でなければなりません。
