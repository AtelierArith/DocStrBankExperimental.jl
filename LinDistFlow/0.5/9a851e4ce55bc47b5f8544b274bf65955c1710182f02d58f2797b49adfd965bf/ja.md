```
constrain_loads(m, p::Inputs)
```

  * Inputs.Ploadの負の値に負荷を設定し、Inputsを作成する際にSbaseで正規化されます
  * PloadのキーはInputs.bussesと一致する必要があります。欠落しているキーは負荷がゼロに設定されます。
  * Inputs.substation_busは制約がなく、スラックバスです

TODO このメソッドはBranchFlowModelの単相と同じです：CommonOPFに移動すべきでしょうか？
