```
wind_profile(z::Number, ustar, d, z0m, psi_m = zero(z); constants)
wind_profile(z, df::AbstractDataFrame, d, z0m, psi_m::AbstractVector; constants)
wind_profile(z, df::DFTable, d, z0m; psi_m = nothing,
  stab_formulation = Dyer1970(), constants)
```

キャノピー上の特定の高さでの風速は、単一レベルの風速測定から推定されます。

# 引数

  * `z`         : 風速が計算される地面からの高さ。
  * `ustar`     : 摩擦速度 (m s-1)
  * `d`         : ゼロ平面変位高さ (-)
  * `z0m`       : 粗さ長 (m)
  * `constants=`[`BigleafConstants`](@ref)`()`

安定性パラメータを供給するDataFrameバリアントの場合

  * `df`:         : 列を持つDataFrame 

      * `ustar`     : 摩擦速度 (m s-1)
  * `psi_m`     : 熱のための安定性関数の値、[`stability_correction`](@ref)を参照。安定性補正を無視するには`psi_m = 0.0`を渡します。

psi_mを推定するDataFrameバリアントの場合

  * `df`の追加列:

      * `Tair`, `pressure`, `H` : [`stability_correction`](@ref)を参照

# 詳細

基礎となる仮定は、d + z0mの高さ（モニン-オブフコフ類似性理論に従って風速が数学的にゼロに達する高さ）以上に対数風プロファイルが存在することです。この場合、特定の高さzでの風速は次のように与えられます：

$$
u(z) = (ustar/k) * (ln((z - d) / z0m) - \psi_m
$$

粗さパラメータであるゼロ平面変位高さ(d)と粗さ長(z0m)は、[`roughness_parameters`](@ref)から近似できます。$\psi_m$は安定性補正です。安定性補正を無視するにはゼロに設定します（推奨されません）。デフォルトでは、[`stability_correction`](@ref)を使用して風プロファイルから推定されます。

# 注意

この方程式はz >= d + z0mの場合にのみ有効であり、d + z0mのすぐ上での値を計算することは意味がありません。`heights`内のd + z0mより小さいすべての値は0を返します。

# 値

特定の高さ`z`での風速。

# 参考文献

  * Monteith, J*L., Unsworth, M*H., 2008: Principles of Environmental Physics. 3rd edition. Academic Press, London.
  * Newman, J*F., Klein, P*M., 2014: The impacts of atmospheric stability on the accuracy of wind speed extrapolation methods. Resources 3, 81-105.

# 参照

[`roughness_parameters`](@ref)

```jldoctest; output = false
using DataFrames
heights = 18:2:40  # 風速を計算するための地面上の高さ
df = DataFrame(
  Tair=25.0,pressure=100.0,wind=[3.0,4,5],ustar=[0.5,0.6,0.65],H=[200.0,230,250]) 
zr=40;zh=25;d=16
# z0mとMOLは高さに依存せず、事前に計算します
MOL = Monin_Obukhov_length.(df.Tair, df.pressure, df.ustar, df.H)
z0m = roughness_parameters(
  Roughness_wind_profile(), df.ustar, df.wind, df.Tair, df.pressure, df.H; zh, zr).z0m 
ws = map(heights) do z
  wind_profile(z,df,d,z0m; MOL)
end
using Plots # dfの3行の風プロファイルをプロット
plot(first.(ws), heights, ylab = "height (m)", xlab = "wind speed (m/s)", legend=:topleft)
plot!(getindex.(ws, 2), heights)
plot!(getindex.(ws, 3), heights)
nothing
# 出力
```
