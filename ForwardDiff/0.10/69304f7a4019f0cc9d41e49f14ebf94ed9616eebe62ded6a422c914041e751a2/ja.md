```
ForwardDiff.gradient(f, x::AbstractArray, cfg::GradientConfig = GradientConfig(f, x), check=Val{true}())
```

`∇f`を`x`で評価した結果を返します。`f`は`f(x)`として呼び出されると仮定します。配列`∇f`は`x`と同じ形状を持ち、その要素は`∇f[j, k, ...] = ∂f/∂x[j, k, ...]`です。

このメソッドは`isa(f(x), Real)`であることを仮定しています。

`check`を`Val{false}()`に設定すると、タグチェックが無効になります。これは摂動の混乱を引き起こす可能性があるため、注意して使用する必要があります。
