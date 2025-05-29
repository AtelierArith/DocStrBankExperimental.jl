```
SeisUnPatch(in,out;<キーワード引数>)
```

5Dデータパッチのセットから5Dデータボリュームを再構築します。

# 引数

  * `in::Array{String,1}`: パッチのファイル名を含む配列
  * `out::String`: 再構築されたボリュームのファイル名

# キーワード引数

  * `style="sxsygxgy"`: ビンスタイル。オプション: "mxmyhxhy","mxmyhaz","sxsyhxhy","gxgyhxhy","sxsyhaz","gxgyhaz"
  * `min_isx=0`,`max_isx=0`,`min_isy=0`,`max_isy=0`: ソースのグリッドの極値
  * `min_igx=0`,`max_igx=0`,`min_igy=0`,`max_igy=0`: 受信機のグリッドの極値
  * `min_imx=0`,`max_imx=0`,`min_imy=0`,`max_imy=0`: 中点のグリッドの極値
  * `min_ihx=0`,`max_ihx=0`,`min_ihy=0`,`max_ihy=0`: オフセットのグリッドの極値
  * `min_ih=0`,`max_ih=0`,`min_iaz=0`,`max_iaz=0`: 方位とオフセットのグリッドの極値
  * `it_WL=9e9`,`it_WO=0` : 時間パッチの長さと重複サンプル
  * `ix1_WL=9e9`,`ix1_WO=0`: 最初の空間次元の長さと重複サンプル
  * `ix2_WL=9e9`,`ix2_WO=0`,`ix3_WL=9e9`,`ix3_WO=0`,`ix4_WL=9e9`,`ix4_WO=0`
  * `nt=0`: 再構築されたキューブの時間サンプル
  * `ang=90`: 東からの度数で測定されたインライン方向
  * `gamma=1`: PS漸近変換点収集のvp/vs比（PPデータにはgamma=1を使用）
  * `osx=0`,`osy=0`,`ogx=0`,`ogy=0` : ソースと受信機の座標系の原点
  * `omx=0`,`omy=0`,`ohx=0`,`ohy=0`: 中点とオフセットの座標系の原点
  * `oaz=0`,`oh=0` : 方位とオフセットの座標系の原点
  * `dsx=1`,`dsy=1`,`dgx=1`,`dgy=1`: ソースと受信機のステップサイズ
  * `dmx=1`,`dmy=1`,`dhx=1`,`dhy=1`: 中点とオフセットのステップサイズ
  * `dh=1`,`daz=1`: オフセットと方位のステップサイズ

# 出力

ファイル `out` に、5D再構築ボリュームが作成されます。

*クレジット: A. Stanton, F Carozzi, 2017*
