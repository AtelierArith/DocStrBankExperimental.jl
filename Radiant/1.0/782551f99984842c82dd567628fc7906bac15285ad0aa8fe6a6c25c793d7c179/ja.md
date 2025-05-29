```
ジオメトリ
```

輸送計算のための媒体のジオメトリ特性を定義するために使用される構造体。

# 必須フィールド

  * `name::String` : ジオメトリ構造体の名前（または識別子）。
  * `dimension::Int64` : ジオメトリの次元。
  * `material_per_region::Array{Material}` : 各領域ごとの材料の多次元配列。
  * `boundary_conditions::Dict{String,Int64}` : 各軸に沿った境界条件。
  * `number_of_regions::Dict{String,Int64}` : 各軸に沿った領域の数。
  * `voxels_per_region::Dict{String,Vector{Int64}}` : 各軸に沿った各領域内のボクセルの数。
  * `region_boundaries::Dict{String,Vector{Float64}}` : 各軸に沿った各領域の境界。

# オプションフィールド - デフォルト値付き

  * `type::String="cartesian"` : ジオメトリのタイプ。
