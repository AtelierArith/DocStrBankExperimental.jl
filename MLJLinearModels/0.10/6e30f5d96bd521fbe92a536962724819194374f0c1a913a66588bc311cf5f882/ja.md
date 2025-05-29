```julia
struct LPPenalty{p} <: MLJLinearModels.AtomicPenalty
```

パラメータベクトルのスケーリングされたL-pノルム。

$$
P(θ) = ||θ||_{p}^{p}/p
$$

スケーリングは一般的なL2の場合の式を簡素化します。
