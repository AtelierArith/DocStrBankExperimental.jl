```
Climate <: RasterDataSet
```

気候データセット。これらは通常、特定の日付ではなく、年の月であり、`getraster`で`month`キーワードを使用します。また、過去/未来のシナリオでは`date`を使用します。

現在、WorldClimおよびCHELSAに対して`WorldClim{Climate}`、`CHELSA{Climate}`、および`CHELSA{Future{Climate, args..}}`として実装されています。

実装の詳細については、[`getraster`](@ref)ドキュメントを参照してください。
