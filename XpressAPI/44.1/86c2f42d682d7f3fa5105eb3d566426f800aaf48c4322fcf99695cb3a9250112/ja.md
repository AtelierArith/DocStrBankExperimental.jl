```
XPRSiisisolations(prob, iis)::prob
```

Irreducible Infeasible Set (IIS) の孤立識別手順を実行します。

この関数は線形問題にのみ適用されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `iis::Integer`: 孤立を識別する必要がある IIS の番号。これは XPRSiisfirst (IIS)、XPRSiisnext (IIS `-n`) または XPRSiisall (IIS `-a`) によって識別されます。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSiisisolations](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSiisisolations.html) のドキュメントも参照してください。
