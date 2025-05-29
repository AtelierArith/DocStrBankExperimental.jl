```
manhattan(data::DataFrame)
```

# 位置引数

  * `data::DataFrame`: マンハッタンプロットに使用する情報を含むDataFrame。

注意、DataFrameには対応する名前の下に以下の値が保存されている必要があります。 pvalues:pval、chromosome:chr。さらに、位置引数がない場合、DataFrameは最初から最後までの塩基対の順序である必要があります。オプションとして、塩基対情報がある場合、位置変数は`pos`と名付けられている必要があります。

```
manhattan(pvalues::AbstractArray, chr::AbstractArray)
```

# 位置引数

  * `pvalues::AbstractArray`: 関連するGWASのp値。塩基対の順序である必要があります。
  * `chr::AbstractArray`: 各p値のための染色体識別子の配列。

pvaluesと順序が一致する必要があります。

```
manhattan(pvalues::AbstractArray, chr::AbstractArray, pos::AbstractArray)
```

# 位置引数

  * `pvalues::AbstractArray`: 関連するGWASのp値。

塩基対と染色体の同じ順序である必要があります。

  * `chr::AbstractArray`: 各p値のための染色体識別子の配列。

pvaluesと位置の順序が一致する必要があります。

  * `pos::AbstractArray`: 各p値/染色体のための塩基対位置の配列。

pvaluesと染色体の順序が一致する必要があります。

# キーワード引数

  * `titles::AbstractString`: プロットのタイトル。デフォルトは「マンハッタンプロット」です。

空白にするには""を入力します。

  * `outfile::AbstractString`: マンハッタンプロットを保存するための出力名。名前は形式で終わる必要があります。

デフォルトは「manhattan.png」です。 .png、.pdf、.svgファイルをサポートします。

  * `dpi::Int64`: pngファイルを保存するためのドット数。高いDPIは

より高い解像度の大きなファイルを生成します。デフォルトのdpiは350です。

  * `xlabel::AbstractString`: xラベルテキストを置き換えるオプション
  * `ylabel::AbstractString`: yラベルテキストを置き換えるオプション
  * `ymax::Union{Float64, Int64}`: プロット上で表現するための指定された最大y値
  * `ystep`: y軸ラベルの目盛りのステップサイズ。デフォルト値は2.5です。
  * `signifline::Union{Float64, Int64}`: 有意性を示すために描画する線。

デフォルトはα = 0.05のボンフェローニ補正p値です。

  * `linecolor::AbstractString`: 有意性線の色。デフォルトは「deepskyblue1」です。
  * `fontsize` 軸ラベルのサイズ。デフォルトは「15pt」です。
  * `pvalvar` p値列名を示す変数（データフレームのみ）。デフォルトは「pval」です。
  * `chrvar` 染色体列名を示す変数（データフレームのみ）。デフォルトは「chr」です。
  * `posvar` BP位置列名を示す変数（データフレームのみ）。デフォルトは「pos」です。
  * `annotatevar` 注釈列名を示す変数（データフレームのみ）。デフォルトは「gene」です。
  * `annotateinds` マンハッタンプロットの注釈として含める行のインデックス。デフォルトは`nothing`です。
