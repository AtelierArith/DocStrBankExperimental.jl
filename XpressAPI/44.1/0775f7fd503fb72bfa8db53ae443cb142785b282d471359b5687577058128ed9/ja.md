```
XPRSmipoptimize(prob, flags)::prob
```

この関数は、最適なMIPソリューションのためのツリー検索を開始します。

最適化の方向はOBJSENSEによって与えられます。関数が完了したときの問題の状態は、MIPSTATUSを使用して確認できます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `flags::Union{Nothing,AbstractString}`: 初期の連続問題を解決する方法を指定するXPRSmipoptimize (MIPOPTIMIZE)に渡すフラグ。MIPエンティティが緩和されています。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSmipoptimize](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSmipoptimize.html)のドキュメントも参照してください。
