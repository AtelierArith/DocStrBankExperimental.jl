```
add_slab!(Phase, Temp, Grid::AbstractGeneralGrid,  trench::Trench; phase = ConstantPhase(1), T = nothing, cell=false)
```

3Dモデルセットアップに相と温度構造を持つ曲がったスラブを追加します。

# パラメータ

  * `Phase`   - 相配列（Gridと一致）
  * `Temp`    - 温度配列（Gridと一致）
  * `Grid`    - グリッド構造（`GMG`の任意のグリッドタイプを使用可能）
  * `trench`  - トレンチ構造
  * `phase`   - ボックスの相を指定します。`ConstantPhase()`,`LithosphericPhases()`を参照
  * `T`       - ボックスの温度を指定します。`ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`,`LithosphericTemp()`を参照
  * `cell`    - trueの場合、`Phase`と`Temp`はセル上で定義されます

# 例

例 1) スラブ

```julia-repl
julia> x     = LinRange(0.0,1200.0,128);
julia> y     = LinRange(0.0,1200.0,128);
julia> z     = LinRange(-660,50,128);
julia> Cart  = CartData(xyz_grid(x, y, z));
julia> Phase = ones(Int64,size(Cart));
julia> Temp  = fill(1350.0,size(Cart));
# トレンチを定義します：
julia> trench= Trench(Start = (400.0,400.0), End = (800.0,800.0), θ_max = 45.0, direction = 1.0, n_seg = 50, Length = 600.0, Thickness = 80.0, Lb = 500.0, d_decoupling = 100.0, type_bending =:Ribe)
julia> phase = LithosphericPhases(Layers=[5 7 88], Phases = [2 3 4], Tlab=nothing)
julia> TsHC  = HalfspaceCoolingTemp(Tsurface=20.0, Tmantle=1350, Age=30, Adiabat=0.4)
julia> add_slab!(Phase, Temp, Cart, trench, phase = phase, T = TsHC)
```
