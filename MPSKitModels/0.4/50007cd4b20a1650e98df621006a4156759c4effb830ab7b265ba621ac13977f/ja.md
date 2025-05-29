```
kitaev_model([elt::Type{<:Number}], [lattice::AbstractLattice];
             t=1.0, mu=1.0, Delta=1.0)
```

キタエフモデルのハミルトニアンのMPOは、次のように定義されます。

$$
H = \sum_{\langle i,j \rangle} \left(-\frac{t}{2}(c_i^+ c_j^- + c_j^+c_i^-) + \frac{Δ}{2}(c_i^+c_j^+ + c_j^-c_i^-) \right) - \mu \sum_{i} c_i^+ c_i^-
$$

デフォルトでは、このモデルは単位格子間隔の無限チェーン上で定義され、テンソルのエントリは`ComplexF64`です。
