```
constraints_list(tr::Translation)
```

翻訳された集合の制約のリストを返します。

### 入力

  * `tr` – 多面体の翻訳

### 出力

翻訳の制約のリスト。

### 注意事項

遅延翻訳 `X` によってラップされた集合が `constraints_list(⋅)` メソッドを提供することを前提とします。

### アルゴリズム

翻訳は、すべての `x ∈ X` に対して `y = x + v` となる点の集合によって定義されるとします。次に、各定義半空間 `a⋅x ≤ b` は `a⋅y ≤ b + a⋅v` に変換されます。 ```
