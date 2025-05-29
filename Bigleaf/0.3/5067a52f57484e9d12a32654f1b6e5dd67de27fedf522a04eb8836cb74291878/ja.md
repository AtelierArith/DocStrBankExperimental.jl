```
roughness_parameters(::RoughnessCanopyHeight()    , zh; frac_d=0.7, frac_z0m=0.1)
roughness_parameters(::RoughnessCanopyHeightLAI(), zh, LAI; cd=0.2, hs=0.01)
roughness_parameters(::Roughness_wind_profile()     , ustar, wind, psi_m; 
  zh, zr, d = 0.7*zh, constants)

roughness_parameters(::Roughness_wind_profile(), ustar, wind, Tair, pressure, H; 
  zh, zr, d = 0.7*zh, stab_formulation=Dyer1970(), constants)
roughness_parameters(::Roughness_wind_profile(), df::DFTable; ...)
```

二つの粗さパラメータ、すなわち変位高さ (d) と運動量のための粗さ長 (z0m) の近似。

# 引数

  * `zh`        : 植生の高さ (m)
  * `constants=`[`BigleafConstants`](@ref)`()`:

キャノピーの高さによる:

  * `frac_d`    : キャノピーの高さに対する変位高さの割合 (-)
  * `frac_z0m`  : キャノピーの高さに対する粗さ長の割合 (-)

キャノピーの高さとLAIによる

  * `LAI`       : 葉面積指数 (-)
  * `cd`        : 個々の葉の平均抗力係数。デフォルトは0.2。
  * `hs`        : 土壌表面の粗さ長 (m)。

風速プロファイルによる

  * `wind`      : 高さ zr における風速 (m s-1)
  * `ustar`     : 摩擦速度 (m s-1)
  * `zr`        : 計測器（基準）高さ (m)
  * `d`         : ゼロ平面変位高さ (-)
  * `psi_m`     : 熱の安定性関数の値、[`stability_correction`](@ref)を参照

別の変種では、[`stability_correction`](@ref) によって `psi_m` の推定が行われ、さらなる入力引数が必要です。便宜上、これらの引数はDataFrameを使用して提供できますが、その場合、結果は型安定ではありません。

# 詳細

二つの主要な粗さパラメータ、変位高さ (d) と運動量のための粗さ長 (z0m) は、キャノピーの高さ (zh) との単純な経験的関係から推定できます。`method = RoughnessCanopyHeight()` の場合、以下の式が使用されます:  

$$
d = frac_d * zh
$$

$$
z0m = frac_{z0m} * zh
$$

ここで、$frac_d$ のデフォルトは0.7、$frac_{z0m}$ のデフォルトは0.1です。

また、d と z0m はキャノピーの高さとLAIの両方から推定できます（`method = RoughnessCanopyHeightLAI()` の場合）。Shaw & Pereira 1982 のデータに基づき、Choudhury & Monteith 1988 は以下の半経験的関係を提案しました:

$$
X = cd * LAI
$$

$$
d = 1.1 * zh * \ln(1 + X^{1/4})
$$

$$
z0m = hs + 0.3 * zh * X^{1/2}
$$

for $0 <= X <= 0.2$

$$
z0m = hs * zh * (1 - d/zh)
$$

for $0.2 < X$ 

`method = Roughness_wind_profile()` の場合、z0m は風速プロファイルを解くことによって推定されます:

$$
z0m = \text{median}((zr - d) * \exp(-k*wind / ustar - psi_m)
$$

デフォルトでは、この式の d は 0.7*zh に固定されていますが、他の任意の値に設定することができます。   

# 値

以下のコンポーネントを持つ NamedTuple:

  * `d`: ゼロ平面変位高さ (m)
  * `z0m`: 運動量のための粗さ長 (m)
  * `z0m_se`: `method = wind_profile` の場合のみ: z0m の中央値の標準誤差 (m)

# 参考文献

  * Choudhury, B. J., Monteith J_L., 1988: A four-layer model for the heat budget of homogeneous land surfaces. Q. J. R. Meteorol. Soc. 114, 373-398.
  * Shaw, R. H., Pereira, A., 1982: Aerodynamic roughness of a plant canopy:  a numerical experiment. Agricultural Meteorology, 26, 51-65.

# 参照

[`wind_profile`](@ref)

```jldoctest; output = false
using DataFrames
# estimate d and z0m from canopy height for a dense (LAI=5) and open (LAI=2) canopy
zh = 25.0
roughness_parameters(RoughnessCanopyHeightLAI(),zh,5)
roughness_parameters(RoughnessCanopyHeightLAI(),zh,2)   
   
# fix d to 0.7*zh and estimate z0m from the wind profile
df = DataFrame(
  Tair=[25.0,25.0,25.0],pressure=100.0,wind=[3.0,4.0,5.0],
  ustar=[0.5,0.6,0.65],H=200.0)
roughness_parameters(Roughness_wind_profile(),df;zh,zr=40,d=0.7*zh)

# assume d = 0.8*zh
rp = roughness_parameters(Roughness_wind_profile(),df;zh,zr=40,d=0.8*zh)
≈(rp.z0m, 0.55, rtol=0.1)
# output
true
```
