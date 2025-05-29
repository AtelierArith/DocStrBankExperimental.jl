```
interpolate_point(points_coords::Array{Array{Float64,1},1}, semi, ref_system, sol;
                  smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                  clip_negative_pressure=false)

interpolate_point(point_coords, semi, ref_system, sol;
                  smoothing_length=initial_smoothing_length(ref_system), cut_off_bnd=true,
                  clip_negative_pressure=false)
```

指定された点または点の配列におけるプロパティの補間をTrixiParticlesシミュレーションで実行します。

点の配列（`points_coords`）が与えられた場合、各点を反復処理し、個別に補間を適用します。単一の点（`point_coords`）の場合、その特定の位置で補間を実行します。補間は、近くの粒子からの寄与を重み付けするためにSPHシミュレーションの同じカーネル関数を利用します。

関連情報: [`interpolate_line`](@ref), [`interpolate_plane_2d`](@ref),           [`interpolate_plane_2d_vtk`](@ref), [`interpolate_plane_3d`](@ref), .

# 引数

  * `points_coords`:  プロパティを補間するための点の座標の配列。
  * `point_coords`:   補間のための単一の点の座標。
  * `semi`:           SPHシミュレーションで使用される半離散化。
  * `ref_system`:     SPH粒子のプロパティを定義する参照系。
  * `sol`:            プロパティが補間される現在の解の状態。

# キーワード

  * `smoothing_length=initial_smoothing_length(ref_system)`: 補間に使用されるスムージング長。
  * `cut_off_bnd=true`: 点が流体に対して「近い」境界にある場合、量を`NaN`に設定するかどうかを示すブール値。                     より詳細には、境界がこの点の密度の合計に対して流体よりも多くの影響を持つ場合、すなわち、境界粒子が流体粒子よりも多くのカーネル重み付け質量を加える場合です。
  * `clip_negative_pressure=false`: SPHモデルで一般的なアプローチは負の圧力値をクリップすることですが、これは物理的ではありません。代わりに、ここでは補間中にクリップを行い、ローカルな補間値にのみ影響を与えます。

# 戻り値

  * 複数の点の場合:  各点での補間されたプロパティを含む配列の`NamedTuple`。
  * 単一の点の場合:  点での補間されたプロパティの`NamedTuple`。

# 例

```jldoctest; output = false, filter = r"density = .*", setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), tspan=(0.0, 0.01), callbacks=nothing); ref_system = fluid_system)
# 単一の点の場合
result = interpolate_point([1.0, 0.5], semi, ref_system, sol)

# 複数の点の場合
points = [[1.0, 0.5], [1.0, 0.6], [1.0, 0.7]]
results = interpolate_point(points, semi, ref_system, sol)

# 出力
(density = ...)
```

!!! note
      * この関数は、SPHシミュレーション領域内の指定された線に沿った勾配を分析したり、視覚化を作成したりするのに特に便利です。
      * 補間の精度は、粒子の密度と選択されたスムージング長に依存します。
      * `cut_off_bnd`を使用すると、表面の密度ベースの推定が使用され、実際の表面再構築ほど正確ではありません。

