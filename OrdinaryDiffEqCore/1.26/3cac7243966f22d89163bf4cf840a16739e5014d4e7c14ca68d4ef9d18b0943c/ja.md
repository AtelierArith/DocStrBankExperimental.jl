```
PIController(beta1, beta2)
```

比例-積分（PI）コントローラーは、[`IController`](@ref)と比較して安定性特性が改善された広く使用されているステップサイズコントローラーです。このコントローラーは、OrdinaryDiffEq.jlのほとんどのアルゴリズムのデフォルトです。

次の式に基づいて時間ステップを適応させるPIステップサイズコントローラーを構築します。

```
Δtₙ₊₁ = εₙ₊₁^β₁ * εₙ^β₂ * Δtₙ
```

ここで、`εᵢ`は許容誤差でスケーリングされた誤差推定の逆数です（Hairer, Nørsett, Wanner, 2010, セクションIV.2）。ステップサイズ係数は安全係数`gamma`で乗算され、区間`[qmin, qmax]`にクリップされます。推定誤差`integrator.EEst`が1以下である限り、ステップは受け入れられます。それ以外の場合、ステップは拒否され、予測されたステップサイズで再試行されます。

!!! note
    コントローラーが構築される際に、`beta1, beta2`の係数はメソッドの次数によってスケーリングされません。`PIController`の場合、このスケーリングはコントローラーが構築される際に行う必要があります。


## 参考文献

  * Hairer, Nørsett, Wanner (2010) Solving Ordinary Differential Equations II Stiff and Differential-Algebraic Problems [DOI: 10.1007/978-3-642-05221-7](https://doi.org/10.1007/978-3-642-05221-7)
  * Hairer, Nørsett, Wanner (2008) Solving Ordinary Differential Equations I Nonstiff Problems [DOI: 10.1007/978-3-540-78862-1](https://doi.org/10.1007/978-3-540-78862-1)
