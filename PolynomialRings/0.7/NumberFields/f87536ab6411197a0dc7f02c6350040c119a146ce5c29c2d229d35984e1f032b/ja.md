```
S = NumberField(R)
```

Rが数体であることを確認し、`S <: Number` であり、計算がQuotientRingで行われるよりも効率的である新しいデータ型 `S` を返します。

注意: 現在、この関数は `Q` が数体であることを完全には証明していません。もしそうでない場合、結果の環での算術は意味のある結果を与えません。
