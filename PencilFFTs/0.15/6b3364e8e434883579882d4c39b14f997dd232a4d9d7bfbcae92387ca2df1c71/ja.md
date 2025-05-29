```
allocate_output(p::PencilFFTPlan)          -> PencilArray
allocate_output(p::PencilFFTPlan, dims...) -> Array{PencilArray}
allocate_output(p::PencilFFTPlan, Val(N))  -> NTuple{N, PencilArray}
```

与えられたプランの出力データを保持できる未初期化の [`PencilArray`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#PencilArrays.PencilArray) を割り当てます。

`p` がインプレースプランの場合、[`ManyPencilArray`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#PencilArrays.ManyPencilArray) が割り当てられます。

詳細については [`allocate_input`](@ref) を参照してください。
