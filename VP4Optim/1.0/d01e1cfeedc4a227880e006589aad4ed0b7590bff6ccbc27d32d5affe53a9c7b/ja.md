```
par!(mod::Model, new_par::AbstractArray)
```

すべての固定パラメータを `new_par` の値でリセットします。

## デフォルト

  * `new_par` から `val[par_ind]` に値をコピーします（この順序で）。
  * 次に、オプションの二次アクションをトリガーするために [par_changed!](@ref par_changed!) を呼び出します。
  * `nothing` を返します。
