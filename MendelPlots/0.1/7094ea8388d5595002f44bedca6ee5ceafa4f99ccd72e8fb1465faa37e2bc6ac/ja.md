```
qq(pvalues::AbstractArray)
```

# 位置引数

  * `pvalues::AbstractArray`: pvalues。qqプロットで使用するp値を含む一次元配列。

    qq(df::DataFrame)

# 位置引数

  * `df::DataFrame`: qqプロットで使用するp値を含むDataFrame。注意: p値を示すデータフレームの列はpvalと名付けられている必要があります（df[!, :pval]が存在する必要があります）

# キーワード引数

  * `titles::AbstractString`: プロットのタイトル。デフォルトは「QQ Plot of GWAS p-values」です。

空白にするには""を入力してください。

  * `outfile::AbstractString`: QQプロットを保存するための出力名。名前は形式で終わる必要があります。

デフォルトは「qqplot.png」です。 .png、.pdf、および.svgファイルをサポートしています。

  * `dpi::Union{Float64, Int64}`: pngファイルを保存するためのドット数。DPIが高いほど、ファイルサイズが大きくなり、高解像度になります。デフォルトのdpiは350です。
  * `xlabel::AbstractString`: xラベルテキストを置き換えるオプション
  * `ylabel::AbstractString`: yラベルテキストを置き換えるオプション
  * `xmin::Union{Float64, Int64}`: プロット上で表す指定された最小x値
  * `xmax::Union{Float64, Int64}`: プロット上で表す指定された最大x値
  * `ymin::Union{Float64, Int64}`: プロット上で表す指定された最小y値
  * `ymax::Union{Float64, Int64}`: プロット上で表す指定された最大y値
  * `xstep`: x軸ラベルの目盛りのステップサイズ。デフォルト値は1です。
  * `ystep`: y軸ラベルの目盛りのステップサイズ。デフォルト値は2です。
  * `gifdist`: ゲノムインフレーションファクター`λ`を印刷するための右端からの距離。デフォルトは1.0です。
  * `linecolor::AbstractString`: 「通常」ラインの色。デフォルトの色は「赤」です。
  * `dotcolor::AbstractString`: ドットの色。デフォルトの色は「黒」です。
  * `fontsize` 軸ラベルのサイズ。デフォルトは「15pt」です。
  * `pvalvar` p値列名を示す変数（データフレームのみ）。デフォルトは「pval」です。
