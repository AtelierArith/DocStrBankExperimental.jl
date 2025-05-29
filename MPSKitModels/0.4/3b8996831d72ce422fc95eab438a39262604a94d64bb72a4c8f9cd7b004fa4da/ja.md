```
bilinear_biquadratic_model([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
                           [lattice::AbstractLattice]; spin=1, J=1.0, θ=0.0)
```

双線形二次ヘisenbergモデルのハミルトニアンのMPOは、次のように定義されます。

$$
H = J \sum_{\langle i,j \rangle} \left(\cos(\theta) \vec{S}_i \cdot \vec{S}_j + \sin(\theta) \left( \vec{S}_i \cdot \vec{S}_j \right)^2 \right)
$$

ここで、$\vec{S} = (S^x, S^y, S^z)$です。

デフォルトでは、このモデルは無限のチェーン上に定義され、単位格子間隔で、対称性はなく、テンソルのエントリは`ComplexF64`です。
