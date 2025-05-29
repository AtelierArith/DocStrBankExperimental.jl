```
ExpRelaxation(variable, expression [, τ]) <: Process
```

与えられた `expression` に対して `variable` の指数緩和を作成する一般的なプロセスで、時間スケール `τ` を持ちます。次の方程式を作成します：

```
τn*Differential(t)(variable) ~ expression - variable
```

ここで `τn` は新しい名前付き `@parameter` で、値は `τ` で、名前は `τ_($(variable))` です。代わりに `τ` が `nothing` の場合、1 がその代わりに使用されます（これがデフォルトの動作です）。もし `iszero(τ)` であれば、方程式 `variable ~ expression` が代わりに作成されます。

便利な関数

```julia
ExpRelaxation(process, τ)
```

は、既存のプロセス（または方程式）を指数緩和に変換することを可能にし、上記の方程式の `expression` として `rhs(process)` を使用します。
