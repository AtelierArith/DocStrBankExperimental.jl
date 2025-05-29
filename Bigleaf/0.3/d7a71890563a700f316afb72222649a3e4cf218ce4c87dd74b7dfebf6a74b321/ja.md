```
potential_ET(::PriestleyTaylor, Tair, pressure, Rn; G=0.0, S=0.0, ...)
potential_ET(::PriestleyTaylor, Tair, pressure, Rn, G, S; ...)

potential_ET(::PenmanMonteith, Tair, pressure, Rn, VPD, Ga_h;
  G=zero(Tair),S=zero(Tair), ...)
fpotential_ET(::PenmanMonteith, Tair, pressure, Rn, VPD, Ga_h, G, S; ...)

potential_ET!(df, approach; ...)

# 引数

  * `Tair`:      気温 (℃)
  * `pressure`:  大気圧 (kPa)
  * `Rn`:        正味放射 (W m-2)
  * `VPD`:       水蒸気圧不足 (kPa)
  * `Ga`:        熱/水蒸気に対する空気力学的導電率 (m s-1)
  * `df`:        上記の変数を含むデータフレーム
  * `approach`:  使用されるアプローチ: `PriestleyTaylor()` または `PenmanMonteith()` のいずれか。

オプション:

  * `G=0.0`:         地面熱フラックス (W m-2)。デフォルトはゼロ。
  * `S=0.0`:         すべての貯蔵フラックスの合計 (W m-2)。デフォルトはゼロ。
  * `constants=`[`BigleafConstants`](@ref)`()`: 物理定数 (cp, eps, Rd, Rgas)

`PriestleyTaylor` の場合:

  * `alpha = 1.26`:   プリーストリー・テイラー係数

ペンマン・モンティスの場合:

  * `Gs_pot = 0.6`:    潜在的/最大表面導電率 (mol m-2 s-1);
  * `Esat_formula`: [`Esat_from_Tair`](@ref) で使用される式

# 詳細

潜在的蒸発散は、プリーストリー・テイラー (1972) に従って計算されます (`approach = PriestleyTaylor()`):

$\mathit{LE}_{pot} = (\alpha \, \Delta \, (Rn - G - S)) / (\Delta + \gamma)$

$\alpha$ はプリーストリー・テイラー係数、$\Delta$ は飽和水蒸気圧曲線の傾き (kPa K-1)、$\gamma$ は心理的定数 (kPa K-1) です。

`approach = PenmanMonteith()` の場合、潜在的蒸発散はペンマン・モンティス方程式に従って計算されます:

$\mathit{LE}_{pot} = (\Delta \, (R_n - G - S) + \rho \, c_p \, \mathit{VPD} \; G_a) /  (\Delta + \gamma \, (1 + G_a/G_{s pot})$

ここで、$\Delta$ は飽和水蒸気圧曲線の傾き (kPa K-1)、$\rho$ は空気密度 (kg m-3)、$\gamma$ は心理的定数 (kPa K-1) です。$G_{s pot}$ の値は通常、現地で観測された $G_s$ の最大値、例えば成長期内の $G_s$ の $90^{th}$ パーセンタイルです。

地面熱フラックスと貯蔵熱フラックス `G` または `S` はオプションの引数として提供されます。入力明示的なバリアントでは、デフォルトはゼロです。データフレーム引数では、デフォルトは欠損となり、ゼロと仮定され、ログメッセージに表示されます。ビッグリーフ R パッケージとは異なり、欠損値に対処する必要があることに注意してください (例を参照)。

# 値

以下のエントリを持つ NamedTuple:

  * `ET_pot`: 潜在的蒸発散 (kg m-2 s-1)
  * `LE_pot`: 潜在的潜熱フラックス (W m-2)

# 参考文献

  * Priestley, C*H*B., Taylor, R_J., 1972: 大規模パラメータを使用した表面熱フラックスと蒸発の評価について。月刊気象レビュー 100, 81-92.
  * Allen, R*G., Pereira L*S., Raes D., Smith M., 1998: 作物の蒸発散 - 作物の水要求量を計算するためのガイドライン - FAO 灌漑および排水論文 56.
  * Novick, K_A., et al. 2016: 生態系の水と炭素フラックスに対する大気の需要の重要性の増加。自然気候変動 6, 1023 - 1027.

# 参照

[`surface_conductance`](@ref)

# 例

正味放射が 500 Wm-2 の表面の潜在的 ET をプリーストリー・テイラーを使用して計算します:

```

jldoctest; output=false Tair, pressure, Rn = 30.0,100.0,500.0 ET*pot, LE*pot = potential*ET(PriestleyTaylor(), Tair, pressure, Rn)     ≈(ET*pot, 0.000204; rtol = 1e-2)

# output

true

```

Gs (0.5 mol m-2 s-1) と Ga (0.1 m s-1) が既知の表面の潜在的 ET をペンマン・モンティスを使用して計算します:

```

jldoctest; output=false Tair, pressure, Rn = 30.0,100.0,500.0 VPD, Ga*h, Gs*pot = 2.0, 0.1, 0.5 ET*pot, LE*pot = potential*ET(   PenmanMonteith(), Tair,pressure,Rn,VPD, Ga*h; Gs_pot)    

# 逆方程式でクロスチェック

Gs*ms, Gs*mol = surface*conductance(   InversePenmanMonteith(), Tair,pressure,VPD,LE*pot,Rn,Ga*h) Gs*mol ≈ Gs_pot

# output

true

```

欠損を明示的に置き換えるデータフレームバリアント `coalesce.` を使用します:

```

jldoctest; output=false using DataFrames df = DataFrame(   Tair = 20.0:1.0:30.0,pressure = 100.0, Rn = 500.0, G = 105.0, VPD = 2.0,    Ga_h = 0.1)  allowmissing!(df, Cols(:G)); df.G[1] = missing

# 

# G を明示的に提供する必要があります

df*ET = potential*ET!(copy(df), PriestleyTaylor(); G = df.G)     ismissing(df*ET.ET*pot[1])

# 

# coalesce を使用して欠損値をゼロで置き換えます

df*ET = potential*ET!(   copy(df), PriestleyTaylor(); G = coalesce.(df.G, zero(df.G)))     !ismissing(df*ET.ET*pot[1])

# output

true ```
