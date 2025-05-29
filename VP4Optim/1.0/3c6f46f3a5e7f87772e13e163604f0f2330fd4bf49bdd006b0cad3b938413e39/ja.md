```
x!(mod::Model, x_syms::AbstractArray, x_vals::AbstractArray)
```

`x_syms`で指定された変数パラメータを、`x_vals`の値でリセットします。

## デフォルト

  * `x_vals`から関連する場所に値をコピーします。
  * 次に、オプションの二次アクションをトリガーするために[x_changed!](@ref x_changed!)を呼び出します。
  * `nothing`を返します。
