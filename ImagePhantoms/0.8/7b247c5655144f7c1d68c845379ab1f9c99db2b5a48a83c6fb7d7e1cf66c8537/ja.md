```
image = shepp_logan(M, [N,] [case] ; options...)
```

`M×N` の Shepp-Logan ファントムのサンプルを生成する便利なメソッドです。

# 入力

  * `M::Int` : 水平方向のサイズ
  * `N::Int` : 垂直方向のサイズ、デフォルトは `M`
  * `case::EllipsePhantomVersion = SheppLogan()`

# オプション

  * `oversample::Int = 3` (通常)
  * `yflip::Bool = true` (便利のために `y` サンプルを反転します。)
  * `T::Type{<:Number}` デフォルト `Float32` (ただし `BrainWeb` バージョンでは `Int`)
  * `kwargs...` 残りのオプションは `ellipse_parameters` に渡されるパラメータです。

# 出力

  * `image` : `M × N` 行列

ここでのデフォルトは、両軸に沿って 3 倍のオーバーサンプリング（ピクセルあたり 9 サンプル）ですが、整数インデックスからなる `SheppLoganBrainWeb` ファントムは除きます。
