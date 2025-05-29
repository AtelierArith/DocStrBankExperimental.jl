```
@unitdim(U::UnitSystem,S::UnitSystem) -> dimtext(::typeof(normal(U))) = dimtext(normal(S))
```

`U`の各基底次元に対する`print`出力を、既存の`S`データに基づいて指定してください。

```Julia
@unitdim EMU Gauss
@unitdim ESU Gauss
@unitdim LorentzHeaviside Gauss
@unitdim SI2019 Metric
@unitdim SI1976 Metric
@unitdim CODATA Metric
@unitdim Conventional Metric
@unitdim International Metric
@unitdim InternationalMean Metric
@unitdim Survey English
```

これらの標準例は、組み込みのデフォルトの一部です。
