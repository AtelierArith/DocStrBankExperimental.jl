```
⊗(μs::AbstractMeasure...)
```

`⊗` は積測度を構築するための二項演算子です。これは次の法則を満たします。

```
    basemeasure(μ ⊗ ν) == basemeasure(μ) ⊗ basemeasure(ν)
```
