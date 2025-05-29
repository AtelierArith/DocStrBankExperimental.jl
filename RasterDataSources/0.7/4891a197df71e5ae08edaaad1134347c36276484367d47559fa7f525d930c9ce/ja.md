```
BioClim <: RasterDataSet
```

BioClimデータセット。通常、`1:19`のレイヤーを含んでいます。これらは`:bioX`を使ってもアクセスできます。例えば、`:bio5`です。

通常、`month`や`date`キーワードは使用しませんが、過去/未来のシナリオでは`date`を使用することがあります。

現在、WorldClimとCHELSAに対して`WorldClim{BioClim}`、`CHELSA{BioClim}`、および`CHELSA{Future{BioClim, args..}}`として実装されています。

実装の詳細については、[`getraster`](@ref)のドキュメントを参照してください。
