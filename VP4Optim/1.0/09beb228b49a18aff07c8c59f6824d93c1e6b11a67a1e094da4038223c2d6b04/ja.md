```
x!(mod::Model, new_x::AbstractArray)
```

*すべての*変数パラメータを`new_x`の値でリセットします。

## デフォルト

  * `new_x`から`val[x_ind]`に値をコピーします（この順序で）。
  * その後、オプションの二次アクションをトリガーするために[x_changed!](@ref x_changed!)を呼び出します。
  * `nothing`を返します。
