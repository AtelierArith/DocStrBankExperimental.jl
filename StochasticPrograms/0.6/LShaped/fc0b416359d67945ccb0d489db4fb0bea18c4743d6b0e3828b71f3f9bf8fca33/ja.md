```
凸化
```

整数再帰を処理するために凸化を使用するためのファクトリオブジェクト。`LShaped.Optimizer`の`integer_strategy`に渡すか、[`IntegerStrategy`](@ref)属性を設定します。

...

# パラメータ

  * `maximum_iterations::Integer = 1`: 各サブ問題が解決されるたびにカッティングプレーンを生成するのに費やされる反復回数を決定します。
  * `strategy::ConvexificationStrategy = Gomory()`: 凸化戦略を指定します（`Gomory`、`LiftAndProject`、`CuttingPlaneTree`）
  * `optimizer = nothing`: `LiftAndProject`または`CuttingPlaneTree`戦略で補助問題を解決するために使用されるオプティマイザを任意で指定します。

...
