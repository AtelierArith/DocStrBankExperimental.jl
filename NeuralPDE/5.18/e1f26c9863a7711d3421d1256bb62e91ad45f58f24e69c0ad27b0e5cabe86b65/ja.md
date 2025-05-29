```
NNODE(chain, opt, init_params = nothing; autodiff = false, batch = 0,
      additional_loss = nothing, kwargs...)
```

ニューラルネットワークを使用して常微分方程式を解くためのアルゴリズムです。これは、標準の `ODEProblem` のソルバーとして使用される物理インフォームドニューラルネットワークの特殊化です。

!!! warning
    NNODEは、`du = f(u,p,t)` のように、アウトオブプレース形式で書かれたODEのみをサポートします。`f(du,u,p,t)` の形式ではありません。アウトオブプレースとして宣言されていない場合、NNODEはエラーで終了します。


## 位置引数

  * `chain`: `Lux.AbstractLuxLayer` または `Flux.Chain` として定義されたニューラルネットワークアーキテクチャ。`Flux.Chain` は `adapt(FromFluxAdaptor(), chain)` を使用して `Lux` に変換されます。
  * `opt`: ニューラルネットワークをトレーニングするためのオプティマイザー。
  * `init_params`: ニューラルネットワークの初期パラメータ。デフォルトでは `nothing` であり、これによりニューラルネットワークライブラリによって提供されるランダム初期化が使用されます。

## キーワード引数

  * `additional_loss`: ニューラルネットワークの試行解であるphiとニューラルネットワークの重みであるθを引数に取る関数 `additional_loss(phi, θ)`。
  * `autodiff`: PDE演算子の自動微分と数値微分の切り替え。損失関数の逆モードは常に自動微分（Zygote経由）ですが、これは損失関数内の導関数（時間に関する導関数）のためだけです。
  * `batch`: 損失計算のためのバッチサイズ。デフォルトは `true` で、これはニューラルネットワークが値の行ベクトル `t` に同時に適用されることを意味します。つまり、これはニューラルネットワーク評価のためのバッチサイズです。これにはバッチデータに対応したニューラルネットワークが必要です。`false` は、ニューラルネットワークの適用が個々の時間点で一度に行われることを意味します。これは、`batch` が `strategy` に渡される `QuadratureTraining` には適用されず、これは並行して被積分関数を計算できる点の数です。
  * `param_estim`: 常微分方程式のパラメータがニューラルネットワークのパラメータと共に学習されるかどうかを示すブール値。
  * `strategy`: 評価のための点を選択するために使用されるトレーニング戦略。デフォルトの `nothing` は、`dt` が指定されていない場合に QuadGK を使用した `QuadratureTraining` が使用され、`dt` が指定されている場合は `GridTraining` が使用されます。
  * `kwargs`: 追加のキーワード引数は、Optimization.jl の `solve` 呼び出しにスプラットされます。

## 例

```julia
u0 = [1.0, 1.0]
ts = [t for t in 1:100]
(u_, t_) = (analytical_func(ts), ts)
function additional_loss(phi, θ)
    return sum(sum(abs2, [phi(t, θ) for t in t_] .- u_)) / length(u_)
end
alg = NNODE(chain, opt, additional_loss = additional_loss)
```

```julia
f(u,p,t) = cos(2pi*t)
tspan = (0.0, 1.0)
u0 = 0.0
prob = ODEProblem(linear, u0 ,tspan)
chain = Lux.Chain(Lux.Dense(1, 5, Lux.σ), Lux.Dense(5, 1))
opt = OptimizationOptimisers.Adam(0.1)
sol = solve(prob, NNODE(chain, opt), verbose = true, abstol = 1e-10, maxiters = 200)
```

## 解のノート

解は、`saveat` や `dt` などの標準出力ハンドラに従って固定時間点で評価されることに注意してください。ただし、ニューラルネットワークは完全に連続的な解であるため、`sol(t)` は正確な補間です（ニューラルネットワークのトレーニング結果に基づく）。さらに、`OptimizationSolution` は `sol.k` として返され、さらなる分析に使用されます。

## 参考文献

Lagaris, Isaac E., Aristidis Likas, and Dimitrios I. Fotiadis. "Artificial neural networks for solving ordinary and partial differential equations." IEEE Transactions on Neural Networks 9, no. 5 (1998): 987-1000. ```
