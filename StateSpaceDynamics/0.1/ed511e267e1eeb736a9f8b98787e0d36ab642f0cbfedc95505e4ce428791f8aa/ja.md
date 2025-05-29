```
E_Step(ppca::ProbabilisticPCA, X::Matrix{<:AbstractFloat})
```

PPCAのEMアルゴリズムの期待ステップ。詳細についてはBishopの「パターン認識と機械学習」を参照してください。

# 引数:

  * `ppca::ProbabilisticPCA`: PPCAモデル
  * `X::Matrix{<:AbstractFloat}`: データ行列

# 例:

```julia
ppca = ProbabilisticPCA(K=1, D=2)
E_Step(ppca, rand(10, 2))
```
