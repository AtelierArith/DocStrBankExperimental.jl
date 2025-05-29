```
posterior(fx::FiniteGP, y::AbstractVector{<:Real})
posterior(approx::<Approximation>, fx::FiniteGP, y::AbstractVector{<:Real})
posterior(approx::<Approximation>, lfx::LatentFiniteGP, y::AbstractVector)
```

観測値 `y` に基づいて、潜在ガウス過程（`fx.f` または `lfx.fx.f`）の事後分布を構築します。これは、過程の有限射影（`fx` または `lfx`）に対応します。

2つの引数の形式では、これはガウス尤度の下で観測された `y` に対する正確な GP 回帰を記述し、`PosteriorGP` を返します。

3つの引数の形式では、最初の引数は使用する近似（例：`VFE` または ApproximateGPs.jl などの他のパッケージで定義されたもの）を指定し、`ApproxPosteriorGP` を返します。
