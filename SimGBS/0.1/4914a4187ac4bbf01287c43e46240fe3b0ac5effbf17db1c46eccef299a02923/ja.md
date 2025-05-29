```
GBS(totalQTL, totalSNP, muDensity, sigmasqDensity, winSize, muAlleleFreq, sigmasqAlleleFreq, re, meanDepth, barcodeFile, useChr, plotOutput, writeOutput, onlyOutputGBS)
```

ジェノタイピング・バイ・シーケンシング（GBS）データをシミュレートします。

この関数は、ゲノム変異を*in silico* 消化されたゲノム断片に挿入し、多型配列をバーコードと結合し、シーケンシング深度に基づいて複製することによってGBSリードを生成します。

# 引数

  * `totalQTL`: シミュレートするQTLの総数
  * `totalSNP`: シミュレートするSNPの総数（密度に基づいてSNP位置をサンプリングする場合は「0」に設定）
  * `muDensity`: ログ-ラプラス分布の位置パラメータ（SNP密度のサンプリング用）
  * `sigmasqDensity`: ログ-ラプラス分布のスケールパラメータ（SNP密度のサンプリング用）
  * `winSize`: SNP位置をサンプリングするためのウィンドウとビンのサイズ
  * `muAlleleFreq`: サンプリングされたアレル頻度の平均
  * `sigmasqAlleleFreq`: サンプリングされたアレル頻度の分散
  * `re`: 使用する制限酵素
  * `barcodeFile`: GBSバーコードを含むファイル
  * `useChr`: シミュレートする染色体の数またはセット
  * `plotOutput`: グラフィカル出力が必要な場合はtrueに設定
  * `writeOutput`: テキスト出力が必要な場合はtrueに設定
  * `onlyOutputGBS`: GBSデータのみを保持する場合はtrueに設定

# 例

```julia
julia> GBS(100, 0, -2.0, 0.001, 1000000, 0.5, 0.001, [SimGBS.ApeKI], 20.0, "GBS_Barcodes.txt", [1], false, true, true)
```
