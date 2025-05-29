```
compute_Ram(::ResistanceWindProfile(), ustar; 
  zr, d, z0m, psi_h, constants=BigleafConstants())
compute_Ram!(df, method::ResistanceWindProfile();  
  zr, d, z0m, psi_h = df.psi_h, kwargs...)

compute_Ram(::ResistanceWindZr(), ustar, wind)
compute_Ram!(df, method::ResistanceWindZr(); kwargs...)
```

バルク空気力学的伝導率を推定します。

# 引数

  * `ustar`          : 摩擦速度 (m s-1)
  * `df`             : 上記の列を持つデータフレーム
  * `zr`             : 計器（基準）高さ (m)
  * `d`              : ゼロ平面変位高さ (-)、[`roughness_parameters`](@ref) を使用して推定できます
  * `z0m`            : 運動のための粗さ長 (m)。[`roughness_parameters`](@ref) から推定できます
  * `psi_h`          : 熱と水蒸気のための安定性関数の値 (-) [`stability_correction`](@ref) を参照

# 詳細

運動のための空気力学的抵抗 $R_{a_m}$ は次のように与えられます（`Ram_method = ResistanceWindZr()`）:

$$
R_{a_m} = u/{u^*}^2
$$

ここで、uは水平風速です。この定式化は大気の安定性の変化を考慮しており、追加の安定性補正関数を必要としません。

$$
Ra_m
$$

を計算するための代替手法が提供されています（`Ram_method = ResistanceWindProfile()`）:

$$
R_{a_m} = (ln((z_r - d)/z_{0m}) - \psi_h) / (k \, u^*)
$$

粗さパラメータ `z0m` と `d` が不明な場合、[`roughness_parameters`](@ref) を使用して推定できます。引数 `stab_formulation` は、`Ra_m` に対する大気の安定性の影響を考慮するために使用される安定性補正関数を決定します（`Ra_m` は不安定な層化の場合は低く、安定な層化の場合は高くなります）。層化は安定性パラメータ `zeta` $\zeta=(z-d/L)$ に基づいており、ここで `z` は高さ、`d` はゼロ平面変位高さ、`L` はモニン-オブコフ長で、[`Monin_Obukhov_length`](@ref) を使用して計算されます。安定性補正関数は引数 `stab_formulation` によって選択されます。オプションは `Dyer1970()` と `Businger1971()` および `NoStabilityCorrection()` です。

# 注意

他の種の空気力学的伝導率を追加するには、[`add_Ga!`](@ref) を参照してください。

# 値

運動伝達のための空気力学的抵抗 (s m-1) ($Ra_m$)

# 参考文献

  * Verma, S., 1989: 熱、質量、運動の移動に対する空気力学的抵抗。地域的な蒸発散の推定において、IAHS Pub, 177, 13-20.
  * Verhoef, A., De Bruin, H., Van Den Hurk, B., 1997: 稀な植生のためのパラメータ kB^(-1) に関するいくつかの実用的なノート。応用気象学ジャーナル, 36, 560-572.
  * Hicks, B*B., Baldocchi, D*D., Meyers, T*P., Hosker, J*R., Matt, D_R., 1987: 測定された量から乾燥沈着速度を導出するための予備的な複数抵抗ルーチン。水、空気、土壌汚染 36, 311-330.
  * Monteith, J*L., Unsworth, M*H., 2008: 環境物理学の原則。第3版。エルゼビアアカデミックプレス、バーリントン、アメリカ合衆国。

# 参照

[`aerodynamic_conductance!`](@ref), [`add_Ga!`](@ref)
