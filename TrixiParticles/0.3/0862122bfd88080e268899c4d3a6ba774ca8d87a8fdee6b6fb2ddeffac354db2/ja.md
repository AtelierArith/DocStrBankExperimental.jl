```
interpolate_plane_3d(point1, point2, point3, resolution, semi, ref_system, sol;
                     smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                     clip_negative_pressure=false)
```

3D空間内の平面に沿った特性をTrixiParticlesシミュレーションで補間します。補間のための平面は、3D空間内の3つの点によって定義され、指定された解像度が補間点の密度を決定します。

この関数は、3つの点によって定義された平面内の平行四辺形上に均等に間隔を空けた点のグリッドを生成します。

関連情報: [`interpolate_plane_2d`](@ref), [`interpolate_plane_2d_vtk`](@ref),           [`interpolate_line`](@ref), [`interpolate_point`](@ref).

# 引数

  * `point1`:     平面を定義する最初の点。
  * `point2`:     平面を定義する2番目の点。
  * `point3`:     平面を定義する3番目の点。点は共線であってはなりません。
  * `resolution`: グリッド内の隣接する補間点間の距離。
  * `semi`:       シミュレーションに使用される半離散化。
  * `ref_system`: 補間のための基準系。
  * `sol`:        特性が補間される解の状態。

# キーワード

  * `smoothing_length=initial_smoothing_length(ref_system)`: 補間に使用されるスムージング長。
  * `cut_off_bnd=true`: 点が流体に対して「近い」場合に量を`NaN`に設定するかどうかを示すブール値。                     より詳細には、境界がこの点の密度合計に対して流体よりも多くの影響を持つ場合、                     すなわち、境界粒子が流体粒子よりも多くのカーネル加重質量を追加する場合です。
  * `clip_negative_pressure=false`: SPHモデルで一般的なアプローチは負の圧力値をクリップすることですが、これは非物理的です。                                 代わりに、ここでは補間中にクリップを行い、ローカルな補間値にのみ影響を与えます。

# 戻り値

  * 平面内の各点で補間された特性を含む配列の`NamedTuple`。

!!! note
      * 補間の精度は粒子の密度と選択されたスムージング長に依存します。
      * `cut_off_bnd`を使用すると、表面の密度ベースの推定が使用され、実際の表面再構築ほど正確ではありません。


# 例

```jldoctest; output = false, filter = r"density = .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_3d.jl"), tspan=(0.0, 0.01)); ref_system = fluid_system)
# 点 [0.0, 0.0, 0.0], [1.0, 0.0, 0.0], および [0.0, 1.0, 0.0] によって定義された平面を横断して補間
# 解像度は0.1
results = interpolate_plane_3d([0.0, 0.0, 0.0], [1.0, 0.0, 0.0], [0.0, 1.0, 0.0], 0.1, semi, ref_system, sol)

# 出力
(density = ...)
```
