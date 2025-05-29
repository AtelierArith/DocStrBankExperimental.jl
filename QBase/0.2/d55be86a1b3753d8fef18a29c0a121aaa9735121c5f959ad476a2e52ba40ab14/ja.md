量子測定の結果確率を計算します。条件付き確率はボルンの法則によって決定され、$P(i|j) = \text{Tr}[\Pi_i \rho_j]$ となります。ここで、$\Pi_j$ はPOVM要素であり、$\rho_j$ は密度行列です。

単一の `Ket` または `State` の測定：

```
measure(Π :: POVM, ρ :: State) :: Probabilities
measure(Π :: POVM, ψ :: Ket) :: Probabilities
measure(Π :: PVM, ρ :: State) :: Probabilities
measure(Π :: PVM, ψ :: Ket) :: Probabilities
```

`Ket` または `State` タイプのアンサンブルの測定：

```
measure(Π :: POVM, ρ_states :: Vector{<:State}) :: Conditionals
measure(Π :: POVM, ψ_kets :: Vector{<:Ket}) :: Conditionals
measure(Π :: PVM, ρ_states :: Vector{<:State}) :: Conditionals
measure(Π :: PVM, ψ_kets :: Vector{<:Ket}) :: Conditionals
```
