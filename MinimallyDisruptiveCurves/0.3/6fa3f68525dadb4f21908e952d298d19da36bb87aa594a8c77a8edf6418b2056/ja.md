```
l2_hessian(nom_sol)
```

は、loss(θ₀) = 0という仮定の下でL2損失に従ったヘッセ行列を取得します。nom*solは名目ODE問題の解です。ヘッセ行列は、最初の導関数のみを必要とします：それはsum*ij dyi/dθ * dyj/dthetaです。
