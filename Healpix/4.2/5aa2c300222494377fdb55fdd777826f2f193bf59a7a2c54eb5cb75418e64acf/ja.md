```
gnomonic(m::HealpixMap{T, O, AA}, projparams = Dict()) where {T <: Number, O, AA}
```

gnomonic 投影のための `project` の高レベルラッパーです。

`projparams` 辞書で設定できるパラメータは以下の通りです：

  * `width`: 画像の幅（ピクセル単位、デフォルト：720ピクセル）
  * `height`: 画像の高さ（ピクセル単位）；指定されていない場合は `width` と等しいと見なされます
  * `center`: 中央のピクセルの位置と向き。3要素のタプルで構成されます：

    1. ピクセルの*緯度*（ラジアン単位）
    2. ピクセルの経度（ラジアン単位）
    3. 画像に適用される回転（ラジアン単位）
  * `fov_rad`: x軸およびy軸に沿った画像のサイズ（ラジアン単位、デフォルト：15°）

# 例

```julia
plot(m, gnomonic, Dict(:fov_rad = deg2rad(1.5), :center = (0, 0, deg2rad(45))))
```
