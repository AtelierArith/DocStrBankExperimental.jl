```
ModelCheckingSolver
```

LTL仕様を持つMDPおよびPOMDPのための確率的モデルチェッカーです。このソルバーは、LTL式とモデルチェックを実行するために使用される基盤となるMDP/POMDP計画アルゴリズムを入力として受け取ります。POMDPs.jlの任意のソルバーをサポートしています。内部的に、このソルバーは離散状態および離散アクションモデルを必要とします。

# フィールド

  * `property::SpotFormula`
  * `solver::Solver` 任意のMDP/POMDPソルバー
  * `tolerance::Float64 = 1e-3`
  * `verbose::Bool = true`
