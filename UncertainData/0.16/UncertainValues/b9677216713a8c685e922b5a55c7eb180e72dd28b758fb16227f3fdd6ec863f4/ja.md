```
ConstrainedUncertainScalarPopulation(values, probs)
ConstrainedUncertainScalarPopulation(values, probs::Vector{Number})
ConstrainedUncertainScalarPopulation(values, probs::Statsbase.AbstractWeights)
```

`ConstrainedUncertainScalarPopulation`は、いくつかの集団メンバー（`values`）と、集団メンバーの相対的重要性を示すいくつかの重み（`probs`）で構成されています（例えば、再サンプリング中）。このタイプの不確実な値は、これらに対して`constrain(uval, sampling_constraint)`を呼び出すことによって生成された制約付き不確実な値で構成されることを意図しています。

これは、集団が制約されていることを示すための便利なタイプです。`UncertainScalarPopulation`と同様に動作します。

異なるタイプの`values`に対して異なるコンストラクタがあります：

  * `values`がスカラー数値のみを含む場合、`values`フィールドは`Vector{Number}`型になります。
  * `values`が1つ以上の不確実な値を含む場合、`values`フィールドは`Vector{AbstractUncertainValue}`型になります。
