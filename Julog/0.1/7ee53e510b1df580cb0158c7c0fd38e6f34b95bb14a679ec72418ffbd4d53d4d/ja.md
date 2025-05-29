```
eval_term(term, env[, funcs])
```

環境を考慮して、Julogの項にあるすべての変数を定数に評価します。可能な限り完全に評価された項を返します。

# 引数

  * `term::Term`: 評価する項。
  * `env::Dict{Var,Term}`: 変数を項にマッピングする環境。
  * `funcs::Dict=Dict()`: 追加のカスタム関数（例：カスタム数学）。
