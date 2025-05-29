```
SeisBinHeaders(in,out; <キーワード引数>)
```

利用可能なグリッド情報を使用して、地震データのヘッダーを順次ビンに分けます。

キーワード引数は、SeisGeometryのキーワード引数と一貫性がある必要があります。

# 引数

  * `in`: 入力ファイル名、不規則にサンプリングされたデータ
  * `out`: 出力ファイル名、規則的にサンプリングされたデータ

# キーワード引数

  * `style="sxsygxgy"`: ビンスタイル。オプション: "mxmyhxhy","mxmyhaz","sxsyhxhy","gxgyhxhy","sxsyhaz","gxgyhaz"
  * `ang=90`: 東からのCC度で測定されたインライン方向
  * `gamma=1`: PS漸近変換点収集のvp/vs比（PPデータにはgamma=1を使用）
  * `osx=0`,`osy=0`,`ogx=0`,`ogy=0` : ソースとレシーバーの座標系の原点
  * `omx=0`,`omy=0`,`ohx=0`,`ohy=0`: 中点とオフセット座標系の原点
  * `oaz=0`,`oh=0` : 方位とオフセット座標系の原点
  * `dsx=1`,`dsy=1`,`dgx=1`,`dgy=1`: ソースとレシーバーのステップサイズ
  * `dmx=1`,`dmy=1`,`dhx=1`,`dhy=1`: 中点とオフセットのステップサイズ
  * `dh=1`,`daz=1`: オフセットと方位のステップサイズ
  * `min_isx=0`,`max_isx=0`,`min_isy=0`,`max_isy=0`: ソースのグリッドの極値
  * `min_igx=0`,`max_igx=0`,`min_igy=0`,`max_igy=0`: レシーバーのグリッドの極値
  * `min_imx=0`,`max_imx=0`,`min_imy=0`,`max_imy=0`: 中点のグリッドの極値
  * `min_ihx=0`,`max_ihx=0`,`min_ihy=0`,`max_ihy=0`: オフセットのグリッドの極値
  * `min_ih=0`,`max_ih=0`,`min_iaz=0`,`max_iaz=0`: 方位とオフセットのグリッドの極値
  * `ntrace=10000`: 一度に処理されるトレースの最大数

# 出力

ファイル `out@headers@` に、ビン分けされたヘッダーが保存されます。

*クレジット: Aaron Stanton,2017*
