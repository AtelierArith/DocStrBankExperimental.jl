```
transverse_field_ising([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
                       [lattice::AbstractLattice]; J=1.0, g=1.0)
```

1次元の[横場イジングモデル](https://en.wikipedia.org/wiki/Transverse-field_Ising_model)のハミルトニアンのためのMPOは、次のように定義されます。

$$
H = -J\left(\sum_{\langle i,j \rangle} \sigma^z_i \sigma^z_j + g \sum_{i} \sigma^x_i \right)
$$

ここで、$\sigma^i$はスピン-1/2のパウリ演算子です。`symmetry`の可能な値は`Trivial`、`Z2Irrep`または`FermionParity`です。

デフォルトでは、モデルは単位格子間隔の無限チェーン上に定義され、`Trivial`対称性を持ち、テンソルのエントリは`ComplexF64`です。
