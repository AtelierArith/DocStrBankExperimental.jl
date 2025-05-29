```
解決策
```

最適化問題に対する抽象的な解決策。

具体的なサブタイプは以下を実装する必要があります：

  * `obj_val`: 解の目的値、通常は数値型
  * `obj_val_valid::Bool`: obj_val が有効かどうかを示す
  * `calc_objective(::Solution)`: 解の目的値を計算して返す
  * `initialize!(::Solution)`: 解を何らかの意味のある方法で初期化する
  * `to_maximize(::Type)`: 最小化の場合、このメソッドは false を返さなければならない
  * `copy!(::Solution, ::Solution)`: 最初の解を2番目の解のコピーにする
  * `copy(::Solution)`: 解の独立したコピーを返す
