```
relativeabundance!(a::AbstractAbundanceTable; kind::Symbol=:fraction)
```

AbstractAbundanceTable内の各サンプルをサンプルの合計に正規化します。

デフォルトでは、列の合計は1.0になります。列の合計を100にするには、`kind=:percent`を使用してください。
