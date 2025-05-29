```
sampler(d::Distribution) -> Sampleable
sampler(s::Sampleable) -> s
```

サンプラーは、効率を向上させるために、しばしば（パラメータ自体ではない）事前計算された量に依存することがあります。そのようなサンプラーが存在する場合、バッチサンプリングに使用されるこの `sampler` メソッドを提供することができます。一般的なフォールバックは `sampler(d::Distribution) = d` です。
