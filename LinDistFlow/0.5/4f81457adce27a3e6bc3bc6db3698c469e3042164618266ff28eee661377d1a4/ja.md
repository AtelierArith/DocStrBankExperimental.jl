```
constrain_loads(m, p::Inputs{MultiPhase})
```

  * Inputs.Pload と Qload の負の値に負荷を設定し、Inputs を作成する際に Sbase で正規化されます
  * Pload と Qload のキーは Inputs.busses と一致する必要があります。欠落しているキーは負荷がゼロに設定されます。
  * Inputs.substation_bus は制約がなく、スラックバスです
