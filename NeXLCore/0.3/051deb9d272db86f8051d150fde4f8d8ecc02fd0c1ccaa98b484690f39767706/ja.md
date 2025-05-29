```
stage2image(::Type{DefaultStageMapping}, stage_coord::Dict{Symbol,Any}, centered_coord::Dict{Symbol,Any}, theta::Float64)
```

`stage2image(...)` は `image2stage(...)` の逆関数です。画像の中心のステージ座標 `stage_coord` と、関心のあるピクセルを中心にするステージ座標 `centered_coord` が与えられたとき、ステージが `stage_coord` にあるときの `centered_coordinate` に対応するピクセル座標を計算します。
