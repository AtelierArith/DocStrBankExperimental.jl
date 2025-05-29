```julia
struct ChepigaAnsatz{A<:KrylovKit.KrylovAlgorithm} <: MPSKit.Algorithm
```

MPS基底状態の上に励起を最適化する単一サイト最適化アルゴリズム。

## フィールド

  * `alg::KrylovKit.KrylovAlgorithm`: 固有値ソルバーに使用されるアルゴリズム

## コンストラクタ

```
ChepigaAnsatz()
ChepigaAnsatz(; kwargs...)
ChepigaAnsatz(alg)
```

指定された固有値ソルバーを持つ`ChepigaAnsatz`アルゴリズムを作成するか、キーワード引数を[`Arnoldi`][@extref KrylovKit.Arnoldi]に渡して作成します。

## 参考文献

  * [Chepiga et al. Phys. Rev. B 96 (2017)](@cite chepiga2017)
