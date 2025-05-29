```
quantum_chemistry_hamiltonian(E0::Number, K::AbstractMatrix{<:Number}, V::AbstractArray{<:Number,4}, [elt::Type{<:Number}=ComplexF64])
```

量子化学ハミルトニアンのMPOで、運動エネルギー$K$とポテンシャルエネルギー$V$を持ちます。ハミルトニアンは次のように与えられます。

$$
H = E0 + \sum_{i,j} \sum_s K[i,j] e_{i,s}^{+} e_{j,s}^{-} + \sum_{i,j,k,l} \sum_{s,t} V[i,j,k,l] e_{i,s}^{+} e_{j,t}^{+} e_{k,t}^{-} e_{l,s}^{-}
$$

ここで、$s$と$t$はスピンインデックスで、$\uparrow$または$\downarrow$になります。完全なハミルトニアンは`U₁ ⊠ SU₂ ⊠ FermionParity`対称性を持っています。

!!! note
    これは最先端の量子化学DMRGコードと見なすべきではありません。これは、量子化学のためのMPSKitの使用を示すことを目的としています。特に：

      * 空間群対称性を組み込む試みは行われていません
      * MPSKitには量子化学に必要な多くのアルゴリズム（軌道の順序付け/最適化）が含まれていません
      * MPOHamiltonianは量子化学には適していません


```
