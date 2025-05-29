```
ScaledWeightedCov(wtsm::AbstractMatrix{T})
```

!!! 警告     実験的

スケーリングされた加重共分散行列で、`wtsm` - `NxN` ブロック内相関行列 (N - 観測の総数)。 繰り返し効果のみに使用されます。

SWC = ScaledWeightedCov

$$
R = Corr(W) * \sigma_c^2
$$

ここで $Corr(W)$ - 対角相関行列です。

例:

```julia
matwts = Symmetric(UnitUpperTriangular(rand(size(df0,1), size(df0,1))))
lmm = LMM(@formula(var~sequence+period+formulation), df0;
    repeated = VarEffect(@covstr(1|subject), SWC(matwts)))
fit!(lmm)

```

!!! 注

`symmetry` や値に対する `wtsm` のチェックはありません。
