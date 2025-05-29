```
heisenberg_XYZ([elt::Type{<:Number}], [lattice::AbstractLattice];
    Jx=1.0, Jy=1.0, Jz=1.0, spin=1)
```

XYZハイゼンベルクモデルのハミルトニアンのためのMPOは、次のように定義されます。

$$
H = \sum_{\langle i,j \rangle} \left( J^x S_i^x S_j^x + J^y S_i^y S_j^y + J^z S_i^z S_j^z \right)
$$

デフォルトでは、このモデルは単位格子間隔の無限チェーン上で定義され、テンソルのエントリは`ComplexF64`です。
