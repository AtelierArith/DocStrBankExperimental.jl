```
interpolate_line(start, end_, n_points, semi, ref_system, sol; endpoint=true,
                 smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                 clip_negative_pressure=false)
```

TrixiParticlesシミュレーションにおける線に沿ったプロパティを補間します。線の補間は、`start`と`end_`の間に均等に配置されたポイントの系列を生成することによって行われます。`endpoint`が`false`の場合、線は開始点と終了点の間で補間されますが、これらのポイントは含まれません。

参照: [`interpolate_point`](@ref), [`interpolate_plane_2d`](@ref),           [`interpolate_plane_2d_vtk`](@ref), [`interpolate_plane_3d`](@ref)。

# 引数

  * `start`:      線の開始点。
  * `end_`:       線の終了点。
  * `n_points`:   線に沿って補間するポイントの数。
  * `semi`:       シミュレーションに使用される半分の離散化。
  * `ref_system`: 補間のための基準系。
  * `sol`:        プロパティが補間される解の状態。

# キーワード

  * `endpoint=true`: 補間に終了点を含めるか（`true`）除外するか（`false`）のブール値。
  * `smoothing_length=initial_smoothing_length(ref_system)`: 補間に使用されるスムージング長。
  * `cut_off_bnd=true`: ポイントが流体よりも境界に「近い」場合に量を`NaN`に設定するかどうかを示すブール値。                     より詳細には、このポイントの密度の合計において境界が流体よりも多くの影響を持つ場合、すなわち、境界粒子が流体粒子よりも多くのカーネル加重質量を加える場合です。
  * `clip_negative_pressure=false`: SPHモデルにおける一般的なアプローチは負の圧力値をクリップすることですが、これは物理的ではありません。代わりに、ここでは補間中にクリップを行い、ローカルな補間値にのみ影響を与えます。

# 戻り値

  * 線に沿った各ポイントで補間されたプロパティを含む配列の`NamedTuple`。

!!! note
      * この関数は、SPHシミュレーション領域内の指定された線に沿った勾配を分析したり、視覚化を作成したりするのに特に便利です。
      * 補間の精度は粒子の密度と選択されたスムージング長に依存します。
      * `cut_off_bnd`を使用すると、密度に基づく表面の推定が使用され、実際の表面再構築ほど正確ではありません。


# 例

```jldoctest; output = false, filter = r"density = .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), tspan=(0.0, 0.01), callbacks=nothing); ref_system = fluid_system)
# [1.0, 0.0]から[1.0, 1.0]まで5ポイントで線に沿って補間
results = interpolate_line([1.0, 0.0], [1.0, 1.0], 5, semi, ref_system, sol)

# 出力
(density = ...)
```
