```
System(abstract_system; force_units=u"kJ * mol^-1 * nm^-1", energy_units=u"kJ * mol^-1")
```

AtomsBaseの`AbstractSystem`をMollyの`System`に変換します。

`force_units`と`energy_units`は適切に設定する必要があります。AtomsBaseインターフェースに存在しないプロパティ（例：ペアポテンシャル）を追加するには、便利なコンストラクタ`System(sys::System)`を使用します。
