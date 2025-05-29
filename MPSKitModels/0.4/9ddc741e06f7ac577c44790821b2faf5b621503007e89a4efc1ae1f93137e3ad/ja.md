```
heisenberg_XXX([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
                       [lattice::AbstractLattice]; J=1.0, spin=1)
```

各方向に等方的なハイゼンベルグモデルのハミルトニアンのためのMPOは、次のように定義されます。

$$
H = J \sum_{\langle i,j \rangle} \vec{S}_i \cdot \vec{S}_j
$$

ここで、$\vec{S} = (S^x, S^y, S^z)$です。

デフォルトでは、このモデルは無限の鎖上に定義され、単位格子間隔を持ち、対称性はなく、テンソルのエントリは`ComplexF64`です。

[`heisenberg_XXZ`](@ref)および[`heisenberg_XYZ`](@ref)も参照してください。
