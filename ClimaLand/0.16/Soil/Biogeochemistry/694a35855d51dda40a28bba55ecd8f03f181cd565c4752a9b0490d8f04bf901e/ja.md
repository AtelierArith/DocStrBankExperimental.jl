```
make_update_aux(model::SoilCO2Model)
```

土壌CO2方程式のための関数`make_update_aux`の拡張です。この関数は、補助変数`p.soil.variable`をその場で更新する関数を作成して返します。これは、Differential Equations.jlと連携して動作するように書かれています。
