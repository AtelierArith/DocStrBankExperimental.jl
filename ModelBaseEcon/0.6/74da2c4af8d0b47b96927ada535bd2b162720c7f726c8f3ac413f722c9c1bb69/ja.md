```
linearized(model::Model; <arguments>)
```

与えられたモデルの定常状態に関する線形近似モデルを作成します。

### キーワード引数

  * `sstate` - 提供された定常状態解に関して線形化します
  * `deviation`::Bool - 線形化されたモデルが渡されたデータを定常状態からの偏差として扱うかどうか

関連: [`linearize!`](@ref) および [`with_linearized`](@ref)
