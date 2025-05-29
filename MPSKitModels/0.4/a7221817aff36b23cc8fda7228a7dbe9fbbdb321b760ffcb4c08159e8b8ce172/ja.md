```
hubbard_model([elt::Type{<:Number}], [particle_symmetry::Type{<:Sector}],
              [spin_symmetry::Type{<:Sector}], [lattice::AbstractLattice];
              t, U, mu, n)
```

ハバードモデルのハミルトニアンのMPOは、次のように定義されます。

$$
H = -t \sum_{\langle i,j \rangle} \sum_{\sigma} \left( e_{i,\sigma}^+ e_{j,\sigma}^- + c_{i,\sigma}^- c_{j,\sigma}^+ \right) + U \sum_i n_{i,\uparrow}n_{i,\downarrow} - \sum_i \mu n_i
$$

ここで、$\sigma$は$\uparrow$または$\downarrow$の値を取るスピンインデックスであり、$n$はフェルミオン数演算子[`e_number`](@ref)です。

デフォルトでは、このモデルは無限のチェーン上に定義され、単位格子間隔で、対称性はなく、テンソルのエントリは`ComplexF64`です。`particle_symmetry`が`Trivial`でない場合、固定された粒子数密度$n$を課すことができます。
