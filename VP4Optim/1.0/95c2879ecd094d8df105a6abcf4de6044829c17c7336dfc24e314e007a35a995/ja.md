```
par!(mod::Model, p_syms::AbstractArray, p_vals::AbstractArray)
```

`par_syms`で指定された固定パラメータを、`p_vals`の値でリセットします。

## デフォルト

  * `p_vals`から関連する場所に値をコピーします。
  * その後、オプションの二次アクションをトリガーするために[par_changed!](@ref par_changed!)を呼び出します。
  * `nothing`を返します。
