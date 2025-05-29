```
orthographic(m::HealpixMap{T,O}, projparams = Dict()) where {T <: Number,O <: Order}
```

正射投影のための `project` の高レベルラッパーです。

`projparams` 辞書で設定できるパラメータは以下の通りです：

  * `width`: 画像の幅（ピクセル単位、デフォルト: 720 ピクセル）
  * `height`: 画像の高さ（ピクセル単位）；指定されていない場合は `width` と等しいと見なされます
  * `center`: 左側の地球の中央にあるピクセルの位置（*緯度* と経度）。
