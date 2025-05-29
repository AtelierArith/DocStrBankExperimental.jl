```
quantum_potts([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
              [lattice::AbstractLattice]; q=3, J=1.0, g=1.0)
```

量子ポッツモデルのハミルトニアンのMPOは、次のように定義されます。

$$
H = - J \sum_{\langle i,j \rangle} Z_i^\dagger Z_j + Z_i Z_j^\dagger
- g \sum_i (X_i + X_i^\dagger)
$$

ここで、演算子$Z$と$X$は$q$-回転演算子であり、$Z^q = X^q = 1$および$ZX = \omega XZ$を満たします。ここで、$\omega = e^{2πi/q}$です。
