```julia
fidelity(ρ, σ)

```

2つの密度行列 `ρ` と `σ` の間の忠実度を計算します: $Tr[\sqrt{\sqrt{ρ}σ\sqrt{ρ}}]²$。

# 例

```julia-repl
julia> ρ = PauliVec[1][1]*PauliVec[1][1]'
julia> σ = PauliVec[3][1]*PauliVec[3][1]'
julia> fidelity(ρ, σ)
0.49999999999999944
```
