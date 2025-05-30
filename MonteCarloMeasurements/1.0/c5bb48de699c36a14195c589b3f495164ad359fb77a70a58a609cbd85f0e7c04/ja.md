このパッケージは、モンテカルロ法を用いて確率分布を扱うことを容易にし、関数を通じて確率分布の伝播を可能にします。これは、例えば非線形の[不確実性伝播](https://en.wikipedia.org/wiki/Propagation_of_uncertainty)に役立ちます。変数やパラメータは、データから測定または推定される場合に不確実性と関連付けられることがあります。確率分布を表現するために、`Particles`と`StaticParticles`の2つのコアタイプを提供します。どちらも`<: Real`です。（「Particles」という名前は、[粒子フィルタリング](https://en.wikipedia.org/wiki/Particle_filter)の文献に由来します。）これらのタイプはすべて、浮動小数点数の分布のモンテカルロ近似を形成します。つまり、分布はサンプル/粒子によって表現されます。**相関量**も扱われます。以下の[多変量粒子](https://baggepinnen.github.io/MonteCarloMeasurements.jl/stable/#Multivariate-particles-1)を参照してください。

`Particles`型の数は、計算に参加する際に他の`Number`と同様に振る舞います。Particlesは分布のようにも振る舞うため、計算後には出力の**完全な分布**の近似がキャプチャされ、出力粒子によって表現されます。`mean`、`std`などは、対応する関数`pmean`や`pstd`を使用して粒子から抽出できます。`Particles`は[Distributions.jl](https://github.com/JuliaStats/Distributions.jl)とも相互作用するため、例えば`Normal(p)`を呼び出すと分布から`Normal`型が返され、`fit(Gamma, p)`を使用すると`Gamma`分布が得られます。粒子は、`p`プレフィックスを持つ関数を使用して`maximum/minimum`、`quantile`などを求めることもできます。つまり、`pmaximum`です。粒子を`plot(p)`でプロットすると、ヒストグラムが表示されます。これにはPlots.jlが必要です。カーネル密度推定は、StatsPlots.jlがロードされている場合に`density(p)`で取得できます。

## クイックスタート

```julia
julia> using MonteCarloMeasurements, Plots

julia> a = π ± 0.1 # ± (\pm)を使用してガウス不確実パラメータを構築
Particles{Float64,2000}
 3.14159 ± 0.1

julia> b = 2 ∓ 0.1 # ∓ (\mp)はStaticParticles（StaticArraysを使用）を作成
StaticParticles{Float64,100}
 2.0 ± 0.0999

julia> pstd(a)      # 統計的特性について尋ねる
0.09999231528930486

julia> sin(a)      # 実数のように使用する
Particles{Float64,2000}
 1.2168e-16 ± 0.0995

julia> plot(a)     # プロットする

julia> b = sin.(1:0.1:5) .± 0.1; # 多変量不確実数を作成

julia> plot(b)                   # 粒子のベクトルをプロットできる

julia> using Distributions

julia> c = Particles(500, Poisson(3.)) # 与えられた分布に従って分布された不確実数を作成
Particles{Int64,500}
 2.882 ± 1.7
```

さらなるヘルプについては、[ドキュメント](https://baggepinnen.github.io/MonteCarloMeasurements.jl/stable)、[例のフォルダ](https://github.com/baggepinnen/MonteCarloMeasurements.jl/tree/master/examples)または[arXiv論文](https://arxiv.org/abs/2001.07625)を参照してください。
