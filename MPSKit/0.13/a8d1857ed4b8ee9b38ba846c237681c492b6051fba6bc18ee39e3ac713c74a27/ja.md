```julia
struct TaylorCluster <: MPSKit.Algorithm
```

`N`次の時間発展MPOをテイラークラスタ展開を用いて構築するためのアルゴリズム。

## フィールド

  * `N::Int64`: テイラー展開の次数
  * `extension::Bool`: 高次の補正を含めるかどうか
  * `compression::Bool`: 補正の近似圧縮、次数`N`まで正確

## 参考文献

  * [Van Damme et al. SciPost Phys. 17 (2024)](@cite vandamme2024)
