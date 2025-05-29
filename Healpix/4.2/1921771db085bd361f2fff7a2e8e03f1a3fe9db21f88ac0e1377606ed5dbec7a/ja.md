```
orthographic2(m::HealpixMap{T, O, AA}, projparams = Dict()) where {T <: Number, O, AA}
```

ステレオ正射影のための `project` の高レベルラッパーです。

`projparams` 辞書で設定できるパラメータは以下の通りです：

  * `width`: 画像の幅（ピクセル単位、デフォルト: 720 ピクセル）
  * `height`: 画像の高さ（ピクセル単位）。指定されていない場合は `width` と等しいと見なされます
  * `center`: 左側の地球の中央にあるピクセルの位置（*緯度* と 経度）。デフォルトは (0, 0) です。
