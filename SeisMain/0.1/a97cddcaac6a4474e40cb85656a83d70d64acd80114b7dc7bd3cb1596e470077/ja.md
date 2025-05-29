```
  SeisPatch(in,out;<keyword arguments>)
```

5次元ボリュームから重なり合う5次元パッチを作成します

# 引数

  * `in::String`: 入力ファイル名（データにはヘッダーにグリッド情報が含まれている必要があります）
  * `out::String`: 出力ファイル名のプレフィックス

# キーワード引数

  * `style="sxsygxgy"`: ビンスタイル。オプション: "mxmyhxhy","mxmyhaz","sxsyhxhy","gxgyhxhy","sxsyhaz","gxgyhaz"
  * `min_isx=0`,`max_isx=0`,`min_isy=0`,`max_isy=0`: ソースのためのグリッドの極値
  * `min_igx=0`,`max_igx=0`,`min_igy=0`,`max_igy=0`: 受信機のためのグリッドの極値
  * `min_imx=0`,`max_imx=0`,`min_imy=0`,`max_imy=0`: 中点のためのグリッドの極値
  * `min_ihx=0`,`max_ihx=0`,`min_ihy=0`,`max_ihy=0`: オフセットのためのグリッドの極値
  * `min_ih=0`,`max_ih=0`,`min_iaz=0`,`max_iaz=0`: 方位とオフセットのためのグリッドの極値
  * `it_WL=9e9`,`it_WO=0` : 時間パッチにおける長さと重なり合うサンプル
  * `ix1_WL=9e9`,`ix1_WO=0`: 最初の空間次元における長さと重なり合うサンプル
  * `ix2_WL=9e9`,`ix2_WO=0`,`ix3_WL=9e9`,`ix3_WO=0`,`ix4_WL=9e9`,`ix4_WO=0`

# 出力

`filename,npatch`: データパッチのファイル名、作成されたパッチの数を含む文字列配列

*クレジット: A. Stanton*
