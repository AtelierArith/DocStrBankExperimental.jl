```julia
struct QuasiparticleAnsatz{A, E} <: MPSKit.Algorithm
```

MPS基底状態の上にある準粒子励起のための最適化アルゴリズム。

## フィールド

  * `alg::Any`: 固有値ソルバーに使用されるアルゴリズム
  * `alg_environments::Any`: 準粒子環境に使用されるアルゴリズム

## コンストラクタ

```
QuasiparticleAnsatz()
QuasiparticleAnsatz(; kwargs...)
QuasiparticleAnsatz(alg)
```

与えられたアルゴリズムで`QuasiparticleAnsatz`アルゴリズムを作成するか、キーワード引数を`Arnoldi`に渡すことによって作成します。

## 参考文献

  * [Haegeman et al. Phys. Rev. Let. 111 (2013)](@cite haegeman2013)
