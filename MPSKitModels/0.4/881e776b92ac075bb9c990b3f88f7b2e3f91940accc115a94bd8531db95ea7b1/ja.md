```
bose_hubbard_model([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
                   [lattice::AbstractLattice];
                   cutoff, t, U, mu, n)
```

ボース-ハバードモデルのハミルトニアンのMPOは、次のように定義されます。

$$
H = -t \sum_{\langle i,j \rangle} \left( a_{i}^+ a_{j}^- + a_{i}^- a_{j}^+ \right) - \mu \sum_i N_i + \frac{U}{2} \sum_i N_i(N_i - 1).
$$

ここで、$N$はボソン数演算子[`a_number`](@ref)です。

デフォルトでは、このモデルは無限の鎖上に定義され、単位格子間隔で、対称性はなく、テンソルのエントリは`ComplexF64`です。ヒルベルト空間は、最大で`cutoff`個のボソンが単一のサイトに存在できるように切り捨てられます。`symmetry`が`Trivial`でない場合、固定された（半整数の）粒子数密度`n`を課すことができます。
