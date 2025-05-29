```
K, γ, info = glover_mcfarlane(G::AbstractStateSpace{<:Discrete}, γ = 1.1; W1=1, W2=1, strictly_proper=false)
```

離散システムの場合、`info` タプルにはフィードバックゲイン `F, L` とオブザーバゲイン `Hkf` も含まれており、オブザーバ形式のコントローラは次のように与えられます。

$$
x^+ = Ax + Bu + H_{kf} (Cx - y)\\
u = Fx + L (Cx - y)
$$

このコントローラは*厳密に適切*ではないことに注意してください。すなわち、非ゼロの D 行列を持っています。コントローラはスケーリングされたプラント (`info.Gs`) のオブザーバ形式に変換することができ、`Ko = observer_controller(info)` によって次の関係が成り立ちます `G*K == info.Gs*Ko`（実現は異なります）。

`strictly_proper = true` の場合、返されるコントローラ `K` は `D == 0` になります。これは、計算遅延が存在する実装において有利です。この場合、`info.L == 0` でもあります。

離散版の参考文献: Iglesias, "The Strictly Proper Discrete-Time Controller for the Normalized Left-Coprime Factorization Robust Stabilization Problem"
