```
BioClimPlus <: RasterDataSet
```

CHELSAから入手可能な拡張BioClimデータセット。詳細はCHELSAのウェブサイトをご覧ください: https://chelsa-climate.org/exchelsa-extended-bioclim/

これらのいくつかは、年間の最大、最小、平均、および範囲の平均として利用可能です。他のものは、通常のBioClim変数に似た単一の値を持っています。

通常、`month`や`date`キーワードは使用されませんが、過去/未来のシナリオでは`date`が使用されることがあります。

現在、CHELSAに対して`CHELSA{BioClim}`および`CHELSA{Future{BioClim, args..}}`として実装されており、レイヤー名は`Symbol`として指定されています。

実装の詳細については、[`getraster`](@ref)のドキュメントを参照してください。
