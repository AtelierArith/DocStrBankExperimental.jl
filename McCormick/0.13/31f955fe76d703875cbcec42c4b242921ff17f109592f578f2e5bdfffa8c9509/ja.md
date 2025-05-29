```julia
struct DenseMidInv{S<:VecOrMat{Float64}} <: McCormick.AbstractPreconditionerMC
```

暗黙のマコーミック緩和のための密なLU前処理器。
