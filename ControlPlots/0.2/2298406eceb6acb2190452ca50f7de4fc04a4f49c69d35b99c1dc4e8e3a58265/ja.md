```
plot2d(pos::AbstractVector, reltime; zoom=true, front=false, segments=6, fig="", dz_zoom=1.5, 
       dz=-5.0, dx=-16.0, xlim=nothing, ylim=nothing, xy=nothing)
```

ループ内で `plot2d` を呼び出すことによって、ビデオのような2D粒子システムを表示します。

# 引数

  * `pos`: 3D位置のベクトル。
  * `reltime`: 相対時間。最初に呼び出すときは `0.0` に設定します。
  * `zoom`: ズームを有効にするかどうか（デフォルト: `true`）。
  * `front`: 前面ビューを使用するかどうか（デフォルト: `false`、つまり側面ビュー）。
  * `segments`: テザーセグメントの数（デフォルト: `6`）。
  * `fig`: 表示する図の名前（デフォルト: `""`）。
  * `dz_zoom`: ズームビューでのz軸オフセット（デフォルト: `1.5`）。
  * `dz`: 通常ビューでのz軸オフセット（デフォルト: `-5.0`）。
  * `dx`: x軸オフセット（デフォルト: `-16.0`）。
  * `xlim`: x軸の制限（デフォルト: `nothing`）。
  * `ylim`: y軸の制限（デフォルト: `nothing`）（側面ビューではz軸）。
  * `xy`: テキストのx-y座標（デフォルト: `nothing`）（側面ビューではz軸）。
