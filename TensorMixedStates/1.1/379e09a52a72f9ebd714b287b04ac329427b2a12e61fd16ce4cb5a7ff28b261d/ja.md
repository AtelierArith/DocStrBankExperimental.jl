```
dmrg(hamiltonian, ::State; options...)
dmrg(hamiltonian, ::Simulation; options...)
```

与えられたハミルトニアンの基底状態を、状態/シミュレーションを使用してdmrgで最適化します。

Dmrgは混合表現には対応していないことに注意してください。

# オプション

  * `nsweeps`: スイープの数
  * `observer!`: オブザーバー（`DmrgObserver`を参照）
  * `limits`: mpsに対する制約（`cutoff`と`maxdim`は各スイープに対して異なる値を持つベクトルである可能性があります）
  * その他はITensorMPS.dmrgと同じです
