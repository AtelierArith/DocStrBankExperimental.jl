```
ChepigaAnsatz2 <: Algorithm
```

MPS基底状態の上に励起を行うための二サイト最適化アルゴリズム。

## フィールド

  * `alg::A = Defaults.eigsolver`: 固有値問題に使用するアルゴリズム。
  * `trscheme = Defaults.trscheme`: 切り捨てに使用するアルゴリズム。

## コンストラクタ

```
ChepigaAnsatz2()
ChepigaAnsatz2(; kwargs...)
ChepigaAnsatz2(alg, trscheme)
```

指定された固有値ソルバーと切り捨てを持つ`ChepigaAnsatz2`アルゴリズムを作成するか、キーワード引数を`Arnoldi`に渡すことによって作成します。

## 参考文献

  * [Chepiga et al. Phys. Rev. B 96 (2017)](@cite chepiga2017)
