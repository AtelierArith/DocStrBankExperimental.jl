```
IdealClarifier(states; f_ns = 0, name)
```

理想的クラリファイア。 このシステムは理想的なクラリファイアを定義します。これは静的システムで、物質の保存を確保し、理想的にすべての粒子状化合物を沈殿させます：沈殿しない固体の割合のパラメータを指定できます。流出（排水またはスラッジ）の流量は、[`FlowPump`](@ref)システムなど、次のシステムによって提供される必要があります。

# パラメータ:

  * `states`: クラリファイアが持つべき成分
  * `f_ns`: 沈殿しない固体の割合

# コネクタ:

  * `inflow`: IdealClarifierの流入
  * `effluent`: IdealClarifierの排水
  * `sludge`: IdealClarifierのスラッジ流出
