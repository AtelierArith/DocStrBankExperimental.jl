問題の解決策。

```
(::Solution)(r, t)
(::Solution)(o)
```

解決策を評価します。

# 特性

  * `retcode`: ソルバーの終了ステータス。[`ReturnCode`](https://docs.sciml.ai/SciMLBase/stable/interfaces/Solutions/#retcodes)を参照してください。
  * `i`: 初期値。
  * `b`: 境界値。
  * `d_dob`: 境界での`o`-導関数、ここで`o`はボルツマン変数です。[`o`](@ref)も参照してください。
  * `ob`: 境界定数。[`rb`](@ref)も参照してください。
  * `oi`: `o≥oi`の場合、解は初期値に評価されます。
  * `prob`: 解決された問題。
  * `alg`: 使用されたアルゴリズム。
  * `original`: 該当する場合、元の解決策オブジェクト。
