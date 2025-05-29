```
newton(
    F::AbstractSystem,
    x₀::AbstractVector,
    p = nothing,
    norm::AbstractNorm = InfNorm(),
    cache::NewtonCache = NewtonCache(F);
    options...
)
```

収束基準を指定するためのさまざまなオプションを持つ局所ニュートン法の実装です。[`NewtonResult`](@ref)を返します。計算は常に複素数算術で倍精度で行われ、すなわち`Complex{Float64}`を使用します。オプションの`cache`引数は必要なメモリを事前に割り当てます。これは、メソッドが繰り返し呼び出される場合に便利です。

### オプション

  * `atol::Float64 = 1e-8`: `norm(xᵢ₊₁ - xᵢ) < atol`の場合、メソッドは収束したと見なされます。
  * `rtol::Float64 = atol`: `norm(xᵢ₊₁ - xᵢ) < max(atol, rtol * norm(x₀))`の場合、メソッドは収束したと見なされます。
  * `max_iters::Int = 20`: 最大反復回数。
  * `extended_precision::Bool = false`: `F(x)`の評価に拡張精度をオプションで使用します。これにより、達成可能な精度が向上する可能性があります。
  * `contraction_factor::Float64 = 1.0`: ニュートン更新は$|xᵢ₊₁ - xᵢ| < a^{2^{i-1}}|x₁ - x₀|$を満たさなければなりません（$i ≥ 1$、ここで$a$は`contraction_factor`です）。
  * `min_contraction_iters::Int = typemax(Int)`: `contraction_factor`が満たされなければならない最小反復回数。`min_contraction_iters`回の反復後に収束因子が満たされない場合でも、そのステップは受け入れられます。
  * `max_abs_norm_first_update::Float64 = Inf`: 初期推定値`x₀`は、`norm(x₁ - x₀) >  max_abs_norm_first_update`の場合に拒否されます。
  * `max_rel_norm_first_update::Float64 = max_abs_norm_first_update`: 初期推定値`x₀`は、`norm(x₁ - x₀) >  max_rel_norm_first_update * norm(x₀)`の場合に拒否されます。
