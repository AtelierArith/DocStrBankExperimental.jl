```
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::Data)
```

データが指定されているが、この関数を通じて制約を追加することが望ましくない場合のフォールバックオプション。これは、*e.g.*、容量制約を置き換える必要があるため、`EnergyModelsInvestments`の場合です。
