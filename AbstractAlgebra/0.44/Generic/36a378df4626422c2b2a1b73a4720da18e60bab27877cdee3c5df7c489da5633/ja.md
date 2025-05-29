```
is_submodule(M::AbstractAlgebra.FPModule{T}, N::AbstractAlgebra.FPModule{T}) where T <: RingElement
```

$$
N
$$

が$M$の部分モジュールとして構築された場合は`true`を返します。この関係は推移的に考慮されます（すなわち、部分部分モジュールはこの関係の目的のために部分モジュールと見なされます、など）。モジュール$M$はこの関係のために自分自身の部分モジュールとも見なされます。
