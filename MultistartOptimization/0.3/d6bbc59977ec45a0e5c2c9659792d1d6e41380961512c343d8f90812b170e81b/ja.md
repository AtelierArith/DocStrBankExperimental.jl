`local_minimization(minimization_problem, local_method, x)`

`x`から始めて、`local_method`を使用して局所的な最小化を行います。

目的関数と制約は`minimization_problem`に提供されます。詳細は[`MinimizationProblem`](@ref)を参照してください。`x`は適合する次元の`AbstractVector`である必要があります。

`local_method`は、メソッドが定義されている型であることが推奨されます。ただし、クロージャである場合もあり、その場合は`local_method(minimization_problem, x)`として呼び出されます。

いずれの場合も、次の特性を持つ値を返す必要があります：

  * `location`、最小化点のための`AbstractVector`。
  * `value`、`location`での目的関数の値。非実行可能な領域には`Inf`（または同等のもの）を使用する必要があります。

返される値には他の特性もあるかもしれません。これらは収束診断、デバッグ情報などに役立ちますが、これらは`local_method`に依存します。

`nothing`を返すことは`value == Inf`と同等ですが、場合によっては型推論に対してより良く機能することがあります。なぜなら、メソッドは反事実的な型を構築する必要がないからです。
