```
@unitdim(U::UnitSystem,S::UnitSystem) -> dimtext(::typeof(normal(U))) = dimtext(normal(S))
```

`S`データに基づいて、`U`の各基本次元の`print`出力を指定します。

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
