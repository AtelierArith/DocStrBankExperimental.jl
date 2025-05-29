```
uvit_aphot(imagefile,ds9srcregion, ds9bgdregion[, satu_corr=true, mst_or_bjd="mst"])
```

UVIT FUV/NUV FITS画像に存在するソースのアパーチャフォトメトリーを行います。これはCCDLABパイプラインから取得されたものです。

この関数はDS9のソースおよび背景領域ファイルを使用し、カウントレートを抽出し、飽和の補正を行い、背景のネットカウントレートを計算し、次に[ Tandon et al. (2020)](https://ui.adsabs.harvard.edu/abs/2020AJ....159..158T/abstract)で入手可能なキャリブレーション情報を使用してフラックス密度f_λおよびABマグニチュードに変換します。

ソース領域が円であり、satu*corrがtrueの場合、ソースカウントレートは関数`uvit*saturation_corr.jl`を使用して飽和の補正も行われます（下記参照）。詳細については、[Tandon et al. (2017)](https://ui.adsabs.harvard.edu/abs/2017AJ....154..128T/abstract)を参照してください。

...

# 引数

## 必須パラメータ

  * `imagefile::String`: CCDLABを使用して生成されたFUVまたはNUV画像ファイルの名前（FITS形式）。
  * `ds9srcregfile::String`: ソースのためのds9領域ファイルの名前。
  * `ds9bgdregfile::String`: 背景のためのds9領域ファイルの名前。

## オプションパラメータ

  * `satu_corr::Bool`: true（デフォルト）、ソース抽出領域が円形の場合のみ飽和補正を適用します。点源にのみ有効で、円形抽出領域の半径が約29ピクセルまたは12アーク秒である場合（Tandon et al. 2020を参照）。
  * `mst_or_bjd::String`: ミッション時間またはバリセントリックユリウス日、デフォルト: "mst"。

...
