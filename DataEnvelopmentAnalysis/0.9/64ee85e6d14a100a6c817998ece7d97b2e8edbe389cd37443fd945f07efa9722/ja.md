```
efficiency(model::AbstractEconomicDEAModel)
```

経済DEAモデルの効率スコアを返します。

# オプション引数

  * `type=Economic`: 返す効率スコアのタイプ。

タイプの仕様:

  * `:Economic`: モデルの経済効率を返します。
  * `:Technical`: 技術効率を返します。
  * `:Allocative`: 配分効率を返します。

一部のモデルでは、これらのタイプも許可されています:

  * `:CRS`: 定常規模の下での技術効率を返します。
  * `:VRS`: 変動規模の下での技術効率を返します。
  * `:Scale`: 規模効率を返します。
