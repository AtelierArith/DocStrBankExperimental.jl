```
img = fbp_back(rg, ig, sino ; ia_skip)
```

FBPのための2Dピクセル駆動バックプロジェクション。

# 入力

  * `rg::SinoGeom`
  * `ig::ImageGeom`
  * `sino::AbstractArray{<:Number}` シノグラム（線積分）、通常はランプフィルタリングされている

# オプション

  * `ia_skip::Int` テストのために時間を節約するために角度でダウンサンプリング（デフォルト: 1）

# 出力

  * `img::Array{<:Number}` 再構成された画像
