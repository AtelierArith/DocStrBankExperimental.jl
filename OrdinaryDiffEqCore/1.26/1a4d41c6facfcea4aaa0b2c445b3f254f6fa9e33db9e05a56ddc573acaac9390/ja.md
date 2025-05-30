```
PIDController(beta1, beta2, beta3=zero(beta1);
              limiter=default_dt_factor_limiter,
              accept_safety=0.81)
```

比例-積分-微分（PID）コントローラーは、[`PIController`](@ref) の一般化であり、安定性と効率性の特性が向上する可能性があります。

時間ステップに基づいて適応するPIDステップサイズコントローラーを構築します。式は次の通りです。

```
Δtₙ₊₁ = εₙ₊₁^(β₁/k) * εₙ^(β₂/k) * εₙ₋₁^(β₃/ k) * Δtₙ
```

ここで `k = min(alg_order, alg_adaptive_order) + 1` であり、`εᵢ` は許容誤差でスケーリングされた誤差推定の逆数です（Söderlind, 2003）。ステップサイズの因子は、デフォルト値の `limiter` によって制限されます。

```
limiter(x) = one(x) + atan(x - one(x))
```

これはSöderlindとWang（2006）によって提案されました。予測されたステップサイズの変化が `accept_safety` より大きい場合、ステップは受け入れられます。そうでない場合、ステップは拒否され、予測されたステップサイズで再試行されます。

文献で提案されているいくつかの標準コントローラーのパラメータは次の通りです。

| コントローラー | `beta1` | `beta2` | `beta3` |
|:------- | -------:| -------:|:-------:|
| basic   |  `1.00` |  `0.00` |   `0`   |
| PI42    |  `0.60` | `-0.20` |   `0`   |
| PI33    |  `2//3` | `-1//3` |   `0`   |
| PI34    |  `0.70` | `-0.40` |   `0`   |
| H211PI  |  `1//6` |  `1//6` |   `0`   |
| H312PID | `1//18` |  `1//9` | `1//18` |

!!! note
    [`PIController`](@ref) と対照的に、係数 `beta1, beta2, beta3` はメソッドの次数によってスケーリングされます。したがって、PI42のような標準コントローラーは、異なるアルゴリズムに対して同じ係数 `beta1, beta2, beta3` を使用できます。


!!! note
    他のコントローラーとは異なり、`PIDController` はステップサイズの変化や安全係数 `gamma` を制限するためにキーワード引数 `qmin, qmax` を使用しません。これらの一般的なキーワード引数は、スムーズな動作を保証するために `limiter` と `accept_safety` に置き換えられます（SöderlindとWang、2006）。このため、`PIDController` は [`PIController`](@ref) とは異なる動作をし、たとえ `beta1, beta2` がそれに応じて適応され、`iszero(beta3)` であってもです。


## 参考文献

  * Söderlind (2003) Digital Filters in Adaptive Time-Stepping [DOI: 10.1145/641876.641877](https://doi.org/10.1145/641876.641877)
  * Söderlind, Wang (2006) Adaptive time-stepping and computational stability [DOI: 10.1016/j.cam.2005.03.008](https://doi.org/10.1016/j.cam.2005.03.008) # コントローラー係数
  * Ranocha, Dalcin, Parsani, Ketcheson (2021) # 誤差推定の歴史 Optimized Runge-Kutta Methods with Automatic Step Size Control for   # 予測されたステップサイズの変化がこのパラメータより大きい場合にステップを受け入れる Compressible Computational Fluid Dynamics    # dt因子のリミッター（クリッピング前） [arXiv:2104.06836](https://arxiv.org/abs/2104.06836)
