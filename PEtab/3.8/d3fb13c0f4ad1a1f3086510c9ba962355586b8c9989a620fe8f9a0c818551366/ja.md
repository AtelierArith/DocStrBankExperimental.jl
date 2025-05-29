```
to_prior_scale(xpetab, target::PEtabLogDensity)
```

パラメータ `x` を PEtab 問題スケールから事前スケールに変換します。

この変換はベイズ推論に必要であり、PEtab.jl では事前スケールでベイズ推論が行われます。

!!! note
    この関数を使用するには、Bijectors、LogDensityProblems、および LogDensityProblemsAD パッケージをロードする必要があります: `using Bijectors, LogDensityProblems, LogDensityProblemsAD`

