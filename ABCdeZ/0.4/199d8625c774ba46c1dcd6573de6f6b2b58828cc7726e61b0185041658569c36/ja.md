```
abcdemc!(prior, dist!, ϵ_target, varexternal; <キーワード引数>)
```

マルコフ連鎖モンテカルロセットアップ（mc）での差分進化（de）移動を使用してABCを実行し、事後サンプルを提供します。

アルゴリズムは、偏りのない事後推定のために収束する必要があります。

# 引数

  * `prior`: パラメータの事前分布を指定する `Distribution` または `Factored` オブジェクト。
  * `dist!`: モデルとデータ間の距離を計算する距離関数（`≥ 0.0`）、与えられた `(θ, ve)` 入力（`θ` パラメータ、`ve` 外部変数、`varexternal` を参照）に対して。
  * `ϵ_target`: 最終ターゲット距離（または一般的には、ABCカーネルのターゲット幅）；アルゴリズムは `ϵ_target` に達した場合、最終ターゲット分布（近似事後）に平衡します。
  * `varexternal`: `dist!` に第二の位置引数として渡され、スレッドセーフな方法で高速なインプレース操作で距離計算をサポートするために使用できる外部変数；`varexternal` のオブジェクトは、`parallel` モードでもインプレースで変更可能であり、各スレッドは `varexternal` の独自のコピーを受け取ります（必要ない場合は入力 `nothing`）。
  * `nparticles::Int=50`: 各世代で推論に使用する総粒子数。
  * `generations::Int=20`: アルゴリズムを実行する世代数（総反復回数）。
  * `verbose::Bool=true`: `true` に設定すると、冗長性が有効になります（REPLへの出力）。
  * `rng=Random.GLOBAL_RNG`: 推論に使用される AbstractRNG オブジェクト。
  * `parallel::Bool=false`: `true` に設定すると、スレッド並列処理が有効になります；その場合、`dist!` はスレッドセーフでなければなりません（例：`varexternal`（`ve`）を利用する）。

# 例

```julia-repl
julia> using ABCdeZ, Distributions;
julia> data = 5;
julia> prior = Normal(0, sqrt(10));
julia> model(θ) = rand(Normal(θ, 1));
julia> dist!(θ, ve) = abs(model(θ)-data), nothing;
julia> ϵ = 0.3;
julia> r = abcdemc!(prior, dist!, ϵ, nothing, nparticles=1000, generations=300, parallel=true);
julia> posterior = [t[1] for t in r.P];
```
