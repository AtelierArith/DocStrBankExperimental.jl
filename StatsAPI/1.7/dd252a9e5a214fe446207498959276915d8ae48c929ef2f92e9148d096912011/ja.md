```
bic(model::StatisticalModel)
```

ベイズ情報基準は、$-2 \log L + k \log n$として定義され、ここで$L$はモデルの尤度、$k$は消費された自由度の数（[`dof`](@ref)によって返される）、$n$は観測の数（[`nobs`](@ref)によって返される）です。
