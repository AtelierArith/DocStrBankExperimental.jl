```
BackTracking(; autodiff = nothing, c_1 = 1e-4, ρ_hi = 0.5, ρ_lo = 0.1,
    order = 3,
    maxstep = Inf, initial_alpha = true)
```

`BackTracking` は、[LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl) の実装に基づく線形探索アルゴリズムです。

`BackTracking` は、ステップサイズの減少を決定するために二次または三次の補間を使用するバックトラッキング線形探索を指定します。

例えば、もし `f(α) > f(0) + c₁ α f'(0)` であれば、`f(0)`, `f'(0)`, `f(α)` の二次補間は、開区間 `(0, α)` 内に最小化点 `α'` を持ちます。より強く、ρ = ρ(c₁) という因子が存在して `α' ≦ ρ α` となります。

これは、Nocedal Wright (第2版) の Sec. 3.5 で説明されているアルゴリズムの修正です。

`autodiff` は、線形探索に使用する自動微分バックエンドです。これは、現在のステップサイズでの目的関数の導関数にのみ使用されます。解析的ヤコビアン/jvp/vjpが利用できない場合、`autodiff` を指定する必要があります。
