```
unsafe_comparisons(onoff=true; verbose=true)
```

警告なしで比較関数の使用を切り替えます。デフォルトでは、`mean` が粒子を比較のために浮動小数点数に減らすために使用されます。この関数は変更可能で、例として `set_comparison_function(median)` があります。

```
unsafe_comparisons(mode=:reduction; verbose=true)
```

比較モードを指定することもできます。`mode` は `:safe, :montecarlo, :reduction` の値を取ることができます。`:safe` は `unsafe_comparisons(false)` を呼び出すのと同じで、`:reduction` は `true` に対応します。もし
