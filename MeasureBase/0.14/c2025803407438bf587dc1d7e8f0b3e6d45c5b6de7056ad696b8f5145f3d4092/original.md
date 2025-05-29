```
⊗(μs::AbstractMeasure...)
```

`⊗` is a binary operator for building product measures. This satisfies the law

```
    basemeasure(μ ⊗ ν) == basemeasure(μ) ⊗ basemeasure(ν)
```
