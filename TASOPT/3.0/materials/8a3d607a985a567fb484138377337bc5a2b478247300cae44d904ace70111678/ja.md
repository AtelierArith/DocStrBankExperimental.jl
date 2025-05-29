```
StructuralAlloy(material::String; max_avg_stress = 1.1, safety_factor = 1.0)
```

`StructuralAlloy` 型の外部コンストラクタ。指定された材料は、データベースに以下のデータを持っている必要があります：

  * ρ   : 密度 [kg/m³]
  * E   : ヤング率 [Pa]
  * G   : 剪断弾性率 [Pa]
  * ν   : ポアソン比 [-]
  * σmax: 最大応力（降伏または極限強度） [Pa]
  * τmax: 最大せん断 [Pa]
