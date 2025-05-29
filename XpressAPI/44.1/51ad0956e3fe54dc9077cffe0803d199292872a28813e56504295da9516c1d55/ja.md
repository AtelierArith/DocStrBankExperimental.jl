```
XPRSminim(prob, flags)::prob
```

**非推奨** XPRSlpoptimize または XPRSmipoptimize を代わりに使用するべきです。

最適な LP ソリューションの検索を開始します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `flags::Union{Nothing,AbstractString}`: `XPRSmaxim` (`MAXIM`) または `XPRSminim` (`MINIM`) に渡すフラグ。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSminim](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSminim.html) のドキュメントも参照してください。
