```
autofit_dist(SampleData; DistFit=nothing, FitLib=nothing, sort="AIC", verbose=false)
```

提供されたサンプルデータに対して候補分布のリストをフィットさせ、適合度統計を計算し、結果を要約したDataFrameを返します。

# 引数

  * `SampleData`: サンプルデータの配列。
  * `DistFit` (オプション): 試行する分布タイプの配列（例: `[Normal, Gamma, Exponential]`）。各要素は`Distribution`のサブタイプである必要があります。提供された場合、これは`FitLib`を上書きします。
  * `FitLib` (オプション): 使用する事前定義された分布ライブラリを示すシンボル。有効なオプションには`:all`、`:continuous`、または`:discrete`が含まれます。`DistFit`または`FitLib`が提供されていない場合、デフォルトは`:continuous`です。
  * `sort` (オプション): 結果をソートする基準を示す文字列。オプションには`"ad"`、`"ks"`、`"ll"`、または`"AIC"`が含まれます。デフォルトは`"AIC"`です。
  * `verbose` (オプション): フィットに失敗した分布に対して警告を表示するかどうかを示すブールフラグ。デフォルトは`false`です。

# 戻り値

以下の列を持つDataFrame:

  * `DistName`: 分布タイプの名前。
  * `ADTest`: アンダーソン-ダーリング検定統計。
  * `KSTest`: コルモゴロフ-スミルノフ検定統計。
  * `AIC`: 赤池情報量基準。
  * `AICc`: 修正AIC。
  * `LogLikelihood`: フィットの対数尤度。
  * `FitParams`: フィットした分布のパラメータ。
