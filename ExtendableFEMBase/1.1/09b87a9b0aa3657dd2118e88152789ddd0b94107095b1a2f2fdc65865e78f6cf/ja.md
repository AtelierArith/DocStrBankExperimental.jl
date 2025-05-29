```julia
struct FEVectorBlock{T, Tv, Ti, FEType, APT} <: AbstractArray{T, 1}
```

関連するFESpaceの係数を保持し、AbstractArray（getindex、setindex、size、length）として割り当てることができるFEVectorのブロック
