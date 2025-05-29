```julia
ExpectationProblem(S, g, h, pdist, params)
ExpectationProblem(g, pdist, params)
ExpectationProblem(sm::SystemMap, g, h, d)
```

定義 ∫ g(S(h(x,u0,p)))*f(x)dx

## 引数

𝕏 = 不確実性空間、𝕌 = 初期条件空間、ℙ = モデルパラメータ空間

  * S: 𝕌 × ℙ → 𝕌 システムマップとも呼ばれます。
  * g: 𝕌 × ℙ → ℝⁿᵒᵘᵗ 観測可能量または出力関数とも呼ばれます。
  * h: 𝕏 × 𝕌 × ℙ → 𝕌 × ℙ 共変量関数とも呼ばれます。
  * pdf(d,x): 𝕏 → ℝ 初期状態の不確実性分布。
  * params
