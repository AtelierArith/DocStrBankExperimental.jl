```
TimeDerivative(variable, expression [, τ])
```

`variable`の時間微分を与えられた`expression`に等しくする2番目に簡単なプロセスであり、`Equation`を手動で構築する際のいくつかの便利さを提供します。

新しい`@parameter`をデフォルト値`τ`で構築することによって、方程式`τ_$(variable) Differential(t)(variable) ~ expression`を作成します（`τ`がすでに`@parameter`である場合、それはそのまま使用されます）。`τ`が指定されていない場合は、その場所に1が使用され、パラメータは作成されません。

`iszero(τ)`の場合、プロセス`variable ~ expression`が作成されることに注意してください。
