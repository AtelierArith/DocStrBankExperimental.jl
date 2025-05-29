```
SeisBinData(in,out; <キーワード引数>)
```

既にビンされたトレースヘッダーを使用して、地震データを順次ビンします。入力引数はSeisBinHeadersの入力引数と一貫性がある必要があります。詳細は[`SeisBinHeaders`](@ref)を参照してください。

# 引数

  * `in`: 入力ファイル名、不規則にサンプリングされたデータ
  * `out`: 出力ファイル名、規則的にサンプリングされたデータ

# キーワード引数

  * `style="sxsygxgy"`: ビンスタイル。オプション: "mxmyhxhy","mxmyhaz","sxsyhxhy","gxgyhxhy","sxsyhaz","gxgyhaz"
  * `ang=90`: 東からのCCで測定されたインライン方向の角度
  * `gamma=1`: PS漸近変換点収集のvp/vs比（PPデータにはgamma=1を使用）
  * `osx=0`,`osy=0`,`ogx=0`,`ogy=0` : ソースとレシーバー座標系の原点
  * `omx=0`,`omy=0`,`ohx=0`,`ohy=0`: ミッドポイントとオフセット座標系の原点
  * `oaz=0`,`oh=0` : 方位とオフセット座標系の原点
  * `dsx=1`,`dsy=1`,`dgx=1`,`dgy=1`: ソースとレシーバーのステップサイズ
  * `dmx=1`,`dmy=1`,`dhx=1`,`dhy=1`: ミッドポイントとオフセットのステップサイズ
  * `dh=1`,`daz=1`: オフセットと方位のステップサイズ
  * `min_isx=0`,`max_isx=0`,`min_isy=0`,`max_isy=0`: ソースのグリッド極値
  * `min_igx=0`,`max_igx=0`,`min_igy=0`,`max_igy=0`: レシーバーのグリッド極値
  * `min_imx=0`,`max_imx=0`,`min_imy=0`,`max_imy=0`: ミッドポイントのグリッド極値
  * `min_ihx=0`,`max_ihx=0`,`min_ihy=0`,`max_ihy=0`: オフセットのグリッド極値
  * `min_ih=0`,`max_ih=0`,`min_iaz=0`,`max_iaz=0`: 方位とオフセットのグリッド極値
  * `ntrace=10000`: 一度に処理されるトレースの最大数

# 出力

ファイル`out`に、ビンされたデータが保存されます。

*クレジット: Aaron Stanton, 2017*
