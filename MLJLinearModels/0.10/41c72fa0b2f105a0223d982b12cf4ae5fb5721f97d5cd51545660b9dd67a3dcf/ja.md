```julia
struct LPLoss{p} <: MLJLinearModels.AtomicLoss
```

残差のスケーリングされた L-p 損失。

$$
L(x, y) = ||x-y||_{p}^{p}/p
$$

スケーリングは一般的な L2 ケースでの表現を簡素化します。
