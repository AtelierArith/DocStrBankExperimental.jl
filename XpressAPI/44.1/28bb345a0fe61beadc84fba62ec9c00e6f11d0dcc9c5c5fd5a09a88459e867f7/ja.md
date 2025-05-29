```
XPRSlpoptimize(prob, flags)::prob
```

この関数は最適な連続（LP）解の探索を開始します。

最適化の方向はOBJSENSEによって与えられます。関数が完了したときの問題の状態はLPSTATUSを使用して確認できます。問題内のMIPエンティティは無視されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `flags::Union{Nothing,AbstractString}`: `XPRSlpoptimize`に渡すフラグ（`LPOPTIMIZE`）。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSlpoptimize](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSlpoptimize.html)。
