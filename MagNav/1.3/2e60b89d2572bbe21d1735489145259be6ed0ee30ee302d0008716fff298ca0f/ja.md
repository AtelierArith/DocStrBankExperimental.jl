```
eval_gsa(m::Chain, x, n::Int = min(10000,size(x,1)))
```

モリス法によるグローバル感度分析（GSA）。

参考文献: https://book.sciml.ai/notes/17-Global*Sensitivity*Analysis/

参考文献: https://docs.sciml.ai/GlobalSensitivity/stable/methods/morris/

**引数:**

  * `m`: ニューラルネットワークモデル
  * `x`: `N` x `Nf` データ行列（`Nf` は特徴の数）
  * `n`: （オプション）説明に使用するサンプル（インスタンス）の数

**戻り値:**

  * `means`: 基本効果の平均
