```
ThermalInsulator(material::String)
```

`ThermalInsulator`型の外部コンストラクタ。指定された材料は、データベースに以下のデータを持っている必要があります：

  * ρ (密度)：密度 [kg/m³]
  * conductivity (熱伝導率)：`T`の関数としての熱伝導率を含む文字列 [W/(m⋅K)]
