```
interpolate_plane_2d(min_corner, max_corner, resolution, semi, ref_system, sol;
                     smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                     clip_negative_pressure=false)
```

TrixiParticlesシミュレーションにおける平面に沿った特性を補間します。補間の領域は、左下隅と右上隅によって定義され、指定された解像度が補間点の密度を決定します。

この関数は、定義された領域内に均等に間隔を空けたポイントのグリッドを生成します。

関連情報: [`interpolate_plane_2d_vtk`](@ref), [`interpolate_plane_3d`](@ref),           [`interpolate_line`](@ref), [`interpolate_point`](@ref)。

# 引数

  * `min_corner`: 補間領域の左下隅。
  * `max_corner`: 補間領域の右上隅。
  * `resolution`: グリッド内の隣接する補間点間の距離。
  * `semi`:       シミュレーションに使用される半離散化。
  * `ref_system`: 補間のための基準系。
  * `sol`:        特性が補間される解の状態。

# キーワード

  * `smoothing_length=initial_smoothing_length(ref_system)`: 補間に使用されるスムージング長。
  * `cut_off_bnd=true`: ポイントが流体に対して「近い」場合に量を`NaN`に設定するかどうかを示すブール値。                     より詳細には、境界がこのポイントの密度合計に対して流体よりも多くの影響を持つ場合、すなわち、境界粒子が流体粒子よりも多くのカーネル加重質量を追加する場合です。
  * `clip_negative_pressure=false`: SPHモデルにおける一般的なアプローチは負の圧力値をクリップすることですが、これは物理的ではありません。代わりに、ここでは補間中にクリップを行い、ローカルな補間値にのみ影響を与えます。

# 戻り値

  * 平面内の各ポイントにおける補間された特性を含む配列の`NamedTuple`。

!!! note
      * 補間の精度は粒子の密度と選択されたスムージング長に依存します。
      * `cut_off_bnd`を使用すると、表面の密度ベースの推定が使用され、実際の表面再構築ほど正確ではありません。


# 例

```jldoctest; output = false, filter = r"density = .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), tspan=(0.0, 0.01), callbacks=nothing); ref_system = fluid_system)
# 解像度0.2で[0.0, 0.0]から[1.0, 1.0]までの平面を補間
results = interpolate_plane_2d([0.0, 0.0], [1.0, 1.0], 0.2, semi, ref_system, sol)

# 出力
(density = ...)
```
