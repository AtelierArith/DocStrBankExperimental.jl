```
parallel(data, niter, f = fa)
```

並列分析。

# 引数

  * `data`
  * `niter` は、（正規）ランダムデータ行列を生成し、R、相関行列およびその固有値を計算するシミュレーションのサイズです。
  * `f` 次元削減のための関数。デフォルトは `fa` です。

# 値

  * `real` 読み込んだデータからの固有値。
  * `simulated`, `resampled` シミュレーションデータからの固有値の平均。
  * `simulated_bound`, `resampled_bounds` シミュレーションされた固有値の2.5パーセンタイルおよび97.5パーセンタイルのランク値。
  * `iter` シミュレーションの反復回数。
  * `reduncion_method`
  * `correlation_method`

# 例

```julia
julia> using ParallelAnalysis, Random, StatsPlots
julia> begin Random.seed!(1234)
           a = rand(Uniform(0.5, 2.0), 30)
           b = [sort(rand(Uniform(-3, 3), 4); rev = false) for i in 1:30]
           θ = rand(Normal(0, 1), 3000)
           resp = generate_response(θ, a, b)
       end;

julia> par_fit1 = parallel(resp, 10, x -> fa(x; cor_method = :Polychoric))
Progress: 100%|█████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| Time: 0:00:02
並列分析：
    リサンプリングに基づいて因子の数は1であると提案されました
    リサンプリングに基づいて成分の数は1であると提案されました

julia> plot(par_fit1) # 並列分析の結果を視覚化

julia> plot(par_fit1, markershape = :none) # ノイズのあるマーカーを表示しない。
```
