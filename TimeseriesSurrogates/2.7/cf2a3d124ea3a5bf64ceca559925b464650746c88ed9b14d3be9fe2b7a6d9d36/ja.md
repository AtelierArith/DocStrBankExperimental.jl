```
surrogate(x, method::Surrogate [, rng]) → s
```

与えられた `method` に基づいて、`x` から単一のサロゲート時系列 `s` を作成します。`x` から複数のサロゲートを生成したい場合は、より良いパフォーマンスのために [`surrogenerator`](@ref) を使用するべきです。
