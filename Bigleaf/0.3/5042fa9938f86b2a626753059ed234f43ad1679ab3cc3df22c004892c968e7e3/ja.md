```
  surface_conductance(::FluxGradient,   Tair,pressure,VPD,LE; constants)
  surface_conductance(::InversePenmanMonteith, Tair,pressure,VPD,LE,Rn,Ga_h; 
        G = 0.0, S = 0.0, Esat_formula=Sonntag1990(), constants)

  surface_conductance!(df, method::FluxGradient; kwargs...)
  surface_conductance!(df, method::InversePenmanMonteith; G = 0.0, S = 0.0, kwargs...)
```

水蒸気の表面伝導率を逆ペンマン・モンテス方程式または単純なフラックス勾配アプローチから計算します。

# 引数

  * `Tair`      : 空気温度 (℃)
  * `pressure`  : 大気圧 (kPa)
  * `Rn`        : 正味放射 (W m-2)
  * `df`        : 上記の変数を含むデータフレーム
  * `constants=`[`BigleafConstants`](@ref)`()`: 物理定数を含む辞書

InversePenmanMonteithの追加引数

  * `LE`        : 潜熱フラックス (W m-2)
  * `VPD`       : 水蒸気圧不足 (kPa)
  * `Ga_h`      : 水蒸気に対する空気力学的伝導率 (m s-1)、熱のそれと等しいと仮定
  * `G=0.0`     : 地面の熱フラックス (W m-2)、デフォルトはゼロ
  * `S=0.0`     : すべての貯蔵フラックスの合計 (W m-2)、デフォルトはゼロ
  * `Esat_formula=Sonntag1990()`: [`Esat_from_Tair`](@ref)で使用される式

# 詳細

`InversePenmanMonteith()`の場合、表面伝導率 (Gs) は逆ペンマン・モンテス方程式から m s-1 で計算されます：

$$
G_s = ( LE \. G_a \, \gamma ) / ( \Delta \, A + \rho \, c_p \, G_a \, VPD -  LE \, (\Delta + \gamma ))
$$

ここで、$\gamma$ は心理的定数 (kPa K-1)、$\Delta$ は飽和水蒸気圧曲線の傾き (kPa K^-1)、$\rho$ は空気密度 (kg m-3) です。利用可能エネルギー (A) は $A = R_n - G - S$ と定義されます。

地面の熱フラックスと総貯蔵フラックスは、データフレームの長さのスカラーまたはベクトルとして提供できます。データフレームのバリアントでは、bigleaf R パッケージはデフォルトで `G` と `S` の欠損値を 0 に変換しますが、`Bigleaf.jl` では呼び出し元が注意する必要があります。例えば、`G = coalesce(myGvector, 0.0)` を使用します。

`FluxGradient()`の場合、Gs (mol m-2 s-1) は VPD と ET のみから計算されます：

$$
Gs = ET/p \, VPD
$$

ここで、ET は mol m-2 s-1 で、p は圧力です。この定式化は完全に結合された条件 (すなわち Ga = inf) を仮定しています。この定式化は、McNaughton & Black 1973 の Eq.6 の逆の形に相当します：

$$
Gs = LE \, \gamma / (\rho \, c_p \, VPD)
$$

これにより、Gs は m s-1 で得られます。Gs > Gc (キャノピー伝導率) は、ET の重要な部分が干渉または土壌蒸発から来る条件下で発生します。

`pressure` が利用できない場合は、関数 [`pressure_from_elevation`](@ref) を使用して標高から近似できます。

# 値

エントリを持つ NamedTuple:

  * Gs_ms: m s-1 での表面伝導率
  * Gs_mol: mol m-2 s-1 での表面伝導率

# 参考文献

  * Monteith, J., 1965: Evaporation and environment. In Fogg, G. E. (Ed.), The state and movement of water in living organisms (pp.205-234). 19th Symp. Soc. Exp. Biol., Cambridge University Press, Cambridge
  * McNaughton, K*G., Black, T*A., 1973: A study of evapotranspiration from a Douglas Fir forest using the energy balance approach. Water Resources Research 9, 1579-1590.

# 例

```jldoctest; output = false
Tair,pressure,VPD,LE,Rn,Ga_h,G = (14.8, 97.7, 1.08, 183.0, 778.0, 0.116, 15.6)
Gs = surface_conductance(InversePenmanMonteith(), Tair,pressure,VPD,LE,Rn,Ga_h;G)
isapprox(Gs.Gs_mol, 0.28, atol=0.1)
# output
true
```
