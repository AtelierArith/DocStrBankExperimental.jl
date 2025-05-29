```
ConvectiveAdjustmentVerticalDiffusivity([time_discretization = VerticallyImplicitTimeDiscretization(), FT=Float64;]
                                        convective_κz = 0,
                                        convective_νz = 0,
                                        background_κz = 0,
                                        background_νz = 0)
```

異なる拡散率および/または粘度の値を適用する対流調整垂直拡散率閉じ込めを返します。これは、領域が静的に安定（正またはゼロの浮力勾配）であるか、静的に不安定（負の浮力勾配）であるかによって異なります。

# 引数

  * `time_discretization`: `ExplicitTimeDiscretization()` または `VerticallyImplicitTimeDiscretization()` のいずれか; デフォルトは `VerticallyImplicitTimeDiscretization()`。
  * `FT`: 浮動小数点型; デフォルトは `Float64`。

# キーワード引数

  * `convective_κz`: 負の（不安定な）浮力勾配の領域における垂直トレーサー拡散率。単一の数値、関数、配列、フィールド、または各トレーサーの拡散率のタプルのいずれか。
  * `background_κz`: ゼロまたは正の（安定な）浮力勾配の領域における垂直トレーサー拡散率。
  * `convective_νz`: 負の（不安定な）浮力勾配の領域における垂直粘度。数値、関数、配列、またはフィールドのいずれか。
  * `background_νz`: ゼロまたは正の（安定な）浮力勾配の領域における垂直粘度。

# 例

```jldoctest
julia> using Oceananigans

julia> cavd = ConvectiveAdjustmentVerticalDiffusivity(convective_κz = 1)
ConvectiveAdjustmentVerticalDiffusivity{VerticallyImplicitTimeDiscretization}(background_κz=0.0 convective_κz=1 background_νz=0.0 convective_νz=0.0)
```
