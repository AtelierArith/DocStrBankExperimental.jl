```
XPRSnlpoptimize(prob, flags)::prob
```

SLP問題を最大化または最小化します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `flags::Union{Nothing,AbstractString}`: これらは`XPRSmaxim`および`XPRSminim`と同じ意味を持ちます。

# 戻り値

  * `prob::XPRSprob`: 現在のSLP問題。

C APIの対応する関数[XPRSnlpoptimize](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpoptimize.html)のドキュメントも参照してください。
