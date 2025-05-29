```
stability_correction(zeta; 
  stab_formulation=Dyer1970())
stability_correction(z,d, Tair,pressure,ustar,H; constants,
  stab_formulation=Dyer1970())
stability_correction!(df; zeta, z, d; 
  stab_formulation=Dyer1970(), constants =BigleafConstants())
```

熱と運動量のための統合安定性補正関数

# 引数

  * `zeta`             : 安定性パラメータ zeta (-)
  * `Tair`,`pressure`,`ustar`,`H` : [`Monin_Obukhov_length`](@ref)を参照
  * `z`,`d`            : [`stability_parameter`](@ref)を参照
  * `df`  : [`Monin_Obukhov_length`](@ref)に必要な変数を含むDataFrame
  * `stab_formulation` : 安定性関数の定式化。`Dyer1970()`、`Businger1971()`、または`NoStabilityCorrection()`のいずれか

第二および第三の形式では、[`stability_parameter`](@ref)および[`Monin_Obukhov_length`](@ref)によって`zeta`を計算し、それぞれの引数が必要です。

# 詳細

これらの無次元値は、非中立条件下での指数風プロファイルからの偏差を修正するために必要です。関数は普遍的な関数の統合形式を提供します。これらは安定性パラメータ$\zeta$の値に依存し、高さ`z`の関数であり、[`stability_parameter`](@ref)から計算できます。普遍的な関数の統合は次のようになります：

$$
\psi = -x * \zeta
$$

安定した大気条件下で（$\zeta$ >= 0）、および

$$
\psi = 2 * log( (1 + y(\zeta)) / 2)
$$

不安定な大気条件下で（$\zeta$ < 0）。

異なる定式化は、xとyの値が異なります。

# 値

次の列を持つNamedTuple：

  * `psi_h`: 熱と水蒸気のための安定性関数の値 (-)
  * `psi_m`: 運動量のための安定性関数の値 (-)

# 参考文献

  * Dyer, A_J., 1974: フラックス-プロファイル関係のレビュー。境界層気象学 7, 363-372.
  * Dyer, A. J., Hicks, B_B., 1970: 定常フラックス層におけるフラックス-勾配関係。四半期気象学会誌 96, 715-721.
  * Businger, J_A., Wyngaard, J. C., Izumi, I., Bradley, E. F., 1971: 大気表面層におけるフラックス-プロファイル関係。大気科学ジャーナル 28, 181-189.
  * Paulson, C_A., 1970: 不安定な大気表面層における風速と温度プロファイルの数学的表現。応用気象学ジャーナル 9, 857-861. Foken, T, 2008: 微気象学。シュプリンガー、ベルリン、ドイツ。

# 例

```jldoctest; output = false
using DataFrames
zeta = -2:0.5:0.5
df2 = DataFrame(stability_correction.(zeta; stab_formulation=Businger1971()))                         
propertynames(df2) == [:psi_h, :psi_m]
# output
true
```
