```
convergencerateabstract(Bas::Ulam, D::Dynamic, norms)
```

$$
||L^n|_{U_0}||_s
$$

の強いノルムを`norms`から推定します。これは離散化された演算子の弱いノルムの上限

$$
||L_{h}^n|_{U_0}||_w
$$

に基づいています。

この手法は、Stefano Galatolo、Isaia Nisoli、Benoît Saussolによって開発されました。平衡への収束と脱出率を厳密に推定するための基本的な方法。Journal of Computational Dynamics, 2015, 2 (1) : 51-64. doi: 10.3934/jcd.2015.2.51
