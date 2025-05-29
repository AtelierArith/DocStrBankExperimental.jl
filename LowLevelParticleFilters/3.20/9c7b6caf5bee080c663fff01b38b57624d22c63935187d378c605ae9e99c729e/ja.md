```
sol = forward_trajectory(pf, u::AbstractVector, y::AbstractVector, p=parameters(pf))
```

一連の入力と測定値に対して粒子フィルタを実行します（オフライン / バッチフィルタリング）。`x,w,we,ll = particles, weights, expweights and loglikelihood`を持つ解を返します。

もし[MonteCarloMeasurements.jl](https://github.com/baggepinnen/MonteCarloMeasurements.jl)がロードされている場合、出力粒子を`Matrix{MonteCarloMeasurements.Particles}`に変換することができます。これは`Particles(x,we)`を使用します。内部的には、粒子は再サンプリングされ、すべてが単位重みを持つようになります。これは、[MonteCarloMeasurements.jl](https://baggepinnen.github.io/MonteCarloMeasurements.jl/stable/#Plotting-1)のプロット機能を利用するのに便利です。

`sol`はプロットできます。

```
plot(sol::ParticleFilteringSolution; nbinsy=30, xreal=nothing, dim=nothing)
```
