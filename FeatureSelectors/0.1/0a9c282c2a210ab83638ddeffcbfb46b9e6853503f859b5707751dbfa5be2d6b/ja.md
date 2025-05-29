# FeatureSelectors.jl

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://darrencl.github.io/FeatureSelectors.jl/stable) [![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://darrencl.github.io/FeatureSelectors.jl/dev) [![CI](https://github.com/darrencl/FeatureSelectors.jl/workflows/CI/badge.svg)](https://github.com/darrencl/FeatureSelectors.jl/actions?query=workflow%3ACI) [![Codecov](https://codecov.io/gh/darrencl/FeatureSelectors.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/darrencl/FeatureSelectors.jl)

ターゲット変数との統計的関係に基づいて特徴を選択するためのシンプルなツールです。現在実装されている特徴は以下に基づいています：

  * 相関
  * P値（カイ二乗検定またはF検定によって得られる）

## クイックスタート

```
julia> using RDatasets, FeatureSelectors, DataFrames

julia> boston = dataset("MASS", "Boston");

julia> selector = UnivariateFeatureSelector(method=pearson_correlation, k=5)
UnivariateFeatureSelector(FeatureSelectors.pearson_correlation, 5, nothing)

julia> select_features(
           selector,
           boston[:, Not(:MedV)],
           boston.MedV
       )
5-element Vector{String}:
 "LStat"
 "Rm"
 "PTRatio"
 "Indus"
 "Tax"
```
