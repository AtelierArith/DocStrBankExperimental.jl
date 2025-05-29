```
multiply(shadow1::AbstractShadow, shadow2::AbstractShadow)
```

同じ具体的な型の2つのシャドウオブジェクトを掛け算します。

# 引数:

  * `shadow1::AbstractShadow`: 最初のシャドウオブジェクト。
  * `shadow2::AbstractShadow`: 2番目のシャドウオブジェクト。

# 戻り値

積を表す新しいシャドウオブジェクト。

# 例外

`shadow1`と`shadow2`の型が一致しない場合、`ArgumentError`が発生します。

# 例

```julia
prod_shadow = multiply(shadow1, shadow2)
```
