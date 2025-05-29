```
classical_ising([elt::Type{<:Number}=ComplexF64], [symmetry::Type{<:Sector}=Trivial];
                beta=log(1+sqrt(2))/2)
```

二次元古典イジングモデルの分配関数のためのMPOは、次のように定義されます。

$$
\mathcal{Z}(\beta) = \sum_{\{s\}} \exp(-\beta H(s)) \text{ with } H(s) = -\sum_{\langle i, j \rangle} s_i s_j

$$

ここで、各古典スピンは値$s = \pm 1$を取ることができます。
