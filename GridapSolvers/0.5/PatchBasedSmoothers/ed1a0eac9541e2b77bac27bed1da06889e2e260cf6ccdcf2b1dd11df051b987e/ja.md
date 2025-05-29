```
struct PatchDecomposition{Dr,Dc,Dp} <: DiscreteModel{Dc,Dp}
```

離散モデルのパッチ分解を表します。すなわち、`Ω = Σ_i Ω_i` となるような `Ω` の重なり合うセルカバー `{Ω_i}` です。

## プロパティ:

  * `Dr::Integer` : パッチルートの次元
  * `model::DiscreteModel{Dc,Dp}` : 基本となる離散モデル
  * `patch_cells::Table` : [patch][local cell] -> cell
  * `patch_cells_faces_on_boundary::Table` : [d][overlapped cell][local face] -> face is on patch boundary
