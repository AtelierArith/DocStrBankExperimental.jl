```
uvit_filter2pha(target,imagefile, ds9srcregfile, ds9bgdregfile[,satu_corr=true, respdir=""/soft/astrosat/resp/uvit/"])
```

AstroSat/UVITの広帯域画像からXSPEC/Sherpa互換のソースおよび背景PHAスペクトルファイルを抽出します。これはCCDLAB処理パイプラインから生成されたものです。

この関数は、DS9領域ファイルを使用してソースおよび背景カウントを抽出し、それらをPHAスペクトルファイルに変換します。グレーティングオーダーおよびスペクトル応答の詳細については、[Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract)を参照してください。

...

# 引数

## 必須パラメータ

  * `target::String`: 観測されたUVITフィールドに存在するターゲットの名前。
  * `imagefile::String`: CCDLABを使用して生成されたFITS形式のFUVまたはNUV画像ファイルの名前。
  * `ds9srcregfile::String`: ソース用のds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 背景用のds9領域ファイルの名前。

## オプションパラメータ

  * `satu_corr::Bool`: ポイントソースに対してのみ真の場合に飽和補正を適用します（デフォルト）。
  * `respdir::String`: ローカルマシンにおける応答行列を含むディレクトリの名前。応答ファイルはGitHubページからダウンロードできます。

## 出力

  * ソースおよび背景PHAファイル。
  * 一部の関連情報も画面に表示されます。

...
