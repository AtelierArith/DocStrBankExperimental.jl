```
IController()
```

標準の（積分）コントローラーは、最も基本的なステップサイズコントローラーです。このコントローラーは通常、数値解析のクラスで最初に紹介されますが、多くの問題/アルゴリズムに対する効率の問題から、実際にはめったに使用されるべきではありません。

次の式に基づいて時間ステップを適応させる積分（I）ステップサイズコントローラーを構築します。

```
Δtₙ₊₁ = εₙ₊₁^(1/k) * Δtₙ
```

ここで `k = get_current_adaptive_order(alg, integrator.cache) + 1` であり、`εᵢ` は許容誤差でスケーリングされた誤差推定 `integrator.EEst` の逆数です（Hairer, Nørsett, Wanner, 2008, セクション II.4）。ステップサイズファクターは安全係数 `gamma` で乗算され、区間 `[qmin, qmax]` にクリップされます。推定誤差 `integrator.EEst` が1以下である限り、ステップは受け入れられます。それ以外の場合、ステップは拒否され、予測されたステップサイズで再試行されます。

## 参考文献

  * Hairer, Nørsett, Wanner (2008) Solving Ordinary Differential Equations I Nonstiff Problems [DOI: 10.1007/978-3-540-78862-1](https://doi.org/10.1007/978-3-540-78862-1)
