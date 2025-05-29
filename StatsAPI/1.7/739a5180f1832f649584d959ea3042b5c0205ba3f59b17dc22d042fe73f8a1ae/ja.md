```
aic(model::StatisticalModel)
```

赤池情報量基準（Akaike's Information Criterion）は、$-2 \log L + 2k$として定義され、ここで$L$はモデルの尤度、`k`は消費された自由度の数（[`dof`](@ref)によって返される）です。
