```
x,u,y = simulate(f::AbstractFilter, T::Int, du::Distribution, p=parameters(f), [N]; dynamics_noise=true, measurement_noise=true)
x,u,y = simulate(f::AbstractFilter, u, p=parameters(f); dynamics_noise=true, measurement_noise=true)
```

動的システムを時間 `T` ステップ前方にシミュレートするか、または `u` の期間のためにシミュレートします。状態シーケンス、入力、および測定値を返します。

  * `u` は入力信号の軌跡であり、代わりに `du` はランダム入力の分布です。

シミュレーションは、選択されたノイズモデルによって示されるシステムの進化に関する事前分布からのサンプルと見なすことができます。このようなシミュレーションは、ノイズモデルが合理的であるかどうかを評価するために有用です。

もし [MonteCarloMeasurements.jl](https://github.com/baggepinnen/MonteCarloMeasurements.jl) がロードされている場合、引数 `N::Int` を指定することができ、その場合 `N` 回のシミュレーションが行われ、結果は `Vector{MonteCarloMeasurements.Particles}` の形式で返されます。
