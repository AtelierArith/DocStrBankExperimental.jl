```
aicc(model::StatisticalModel)
```

小標本サイズに対する修正済み赤池情報量基準（Hurvich and Tsai 1989）は、$-2 \log L + 2k + 2k(k-1)/(n-k-1)$として定義され、ここで$L$はモデルの尤度、$k$は消費された自由度の数（[`dof`](@ref)によって返される）、$n$は観測数（[`nobs`](@ref)によって返される）です。
