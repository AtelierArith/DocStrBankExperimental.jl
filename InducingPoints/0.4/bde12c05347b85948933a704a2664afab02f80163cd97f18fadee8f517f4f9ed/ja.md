```
 inducingpoints([rng::AbstractRNG], alg::AIPSA, X::AbstractVector; [kwargs...])
 inducingpoints([rng::AbstractRNG], alg::AIPSA, X::AbstractMatrix; obsdim=1, [kwargs...])
```

アルゴリズム `alg` に従って誘導点を選択します。一部のアルゴリズムでは、追加のキーワード引数が必要です。
