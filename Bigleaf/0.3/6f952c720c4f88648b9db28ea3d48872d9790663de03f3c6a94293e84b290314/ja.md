```
equilibrium_imposed_ET(Tair,pressure,VPD,Gs, Rn; ...)
equilibrium_imposed_ET!(df; ...)
```

蒸発散（ET）は、強制ETと平衡ETに分けられます。

# 引数

  * `Tair`      : 空気温度（℃）
  * `pressure`  : 大気圧（kPa）
  * `VPD`       : 空気の水蒸気圧不足（kPa）
  * `Gs`        : 水蒸気に対する表面伝導率（m s-1）
  * `Rn`        : 正味放射（W m-2）

オプション：

  * `G=0`       : 地面の熱フラックス（W m-2）
  * `S=0`       : すべての貯蔵フラックスの合計（W m-2）
  * `Esat_formula=Sonntag1990()`: [`Esat_from_Tair`](@ref)で使用される式
  * `constants=`[`BigleafConstants`](@ref)`()`: 物理定数（cp, eps）

# 詳細

総蒸発散は次の形で表すことができます（Jarvis & McNaughton 6）：

$$
ET = \Omega \mathit{ET}_{eq} + (1 - \Omega) \mathit{ET}_{imp}
$$

ここで、$\Omega$は[`decoupling`](@ref)から計算されるデカップリング係数です。`ET_eq`は平衡蒸発散、すなわち、放射が支配する条件下で発生するET率です（Ga -> 0のとき）：

$$
ET_{eq} = (\Delta \, (R_n - G - S) \, \lambda) / ( \Delta \gamma)
$$

ここで、$\Delta$は飽和水蒸気圧の傾き（kPa K-1）、$\lambda$は蒸発潜熱（J kg-1）、$\gamma$は心理的定数（kPa K-1）です。`ET_imp`は強制蒸発散率であり、完全に結合された条件下で発生するET率です（Ga -> infのとき）：

$$
ET_{imp} = (\rho \, c_p \, \mathit{VPD} ~ G_s \, \lambda) / \gamma
$$

ここで、$\rho$は空気密度（kg m-3）です。

# 値

次の列を持つ`NamedTuple`または`DataFrame`：

  * `ET_eq`: 平衡ET（kg m-2 s-1）
  * `ET_imp`: 強制ET（kg m-2 s-1）
  * `LE_eq`: 平衡LE（W m-2）
  * `LE_imp`: 強制LE（W m-2）

# 参考文献

  * Jarvis, P*G., McNaughton, K*G., 1986: 蒸散の気孔制御：葉から地域へのスケーリング。生態学的研究の進展1-49。
  * Monteith, J*L., Unsworth, M*H., 2008: 物理の原則。第3版。アカデミックプレス、ロンドン。

# 例

```jldoctest; output = false
Tair,pressure,Rn, VPD, Gs = 20.0,100.0,50.0, 0.5, 0.01
ET_eq, ET_imp, LE_eq, LE_imp = equilibrium_imposed_ET(Tair,pressure,VPD,Gs, Rn)    
≈(ET_eq, 1.399424e-05; rtol = 1e-5)
# output
true
```
