```
image2stage(::Type{DefaultStageMapping}, stage_coord::Dict{Symbol,Any}, img_coord::Dict{Symbol,Any}, theta::Float64)
```

画像の中心にあるステージ座標 `stage_coord`、関心のあるピクセル座標（`stage_coord` と同じ単位）および画像の回転 `theta` を考慮して、ピクセルを画像の中心に持ってくるためのステージ座標を計算します。
