```
ImageParams([T=Float32]; <keyword arguments>) where {T}
```

ImageParamsオブジェクトを構築します。

# 引数:

  * `width=200`: 長方形のグレースケール画像の幅。
  * `height=40`: 長方形のグレースケール画像の高さ。
  * `pad=30`: 画像の周りのパディング。
  * `dist=10`: 画像間の距離。
  * `radius=20`: 校正円の半径。
  * `gray_scale=1000..1000`: グレースケール値の範囲。
  * `calibration_value=nothing`: 校正円の値。指定されていない場合は `gray_scale[2]` になります。
  * `background=nothing`: 背景として使用される値。
  * `hounsfield=false`: グレースケールがハウンズフィールド単位であるべきかどうか。
