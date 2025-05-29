```
project(M::SpecialEuclideanInGeneralLinear, p)
```

点 `p` を [`GeneralLinear`](@ref) から [`SpecialEuclidean`](@ref) 群に射影します。これは、[`affine_matrix`](@ref) のように回転部分と平行移動部分を抽出することによって行われます。
