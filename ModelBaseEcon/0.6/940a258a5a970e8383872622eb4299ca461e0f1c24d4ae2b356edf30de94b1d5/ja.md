```
linearize!(model::Model; <キーワード引数>)
```

モデルを定常状態に関する線形近似に変換します。

### キーワード引数

  * `sstate` - 提供された定常状態解に関して線形化します
  * `deviation`::Bool - 線形化されたモデルが渡されたデータを定常状態からの偏差として扱うかどうか

関連情報: [`linearized`](@ref) と [`with_linearized`](@ref)
