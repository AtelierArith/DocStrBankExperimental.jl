```
abcdesmc!(prior, dist!, ϵ_target, varexternal; <keyword arguments>)
```

ABCを順次モンテカルロセットアップ（smc）で実行し、ポスターサンプルとモデルエビデンスの推定を提供します。 

粒子は有効なポスターサンプルのために（`r.Wns`を介して）重み付けされる必要があります。

# 引数

  * `prior`: パラメータの事前分布を指定する`Distribution`または`Factored`オブジェクト。
  * `dist!`: モデルとデータ間の距離を計算する距離関数（`≥ 0.0`）、与えられた`(θ, ve)`入力（`θ`パラメータ、`ve`外部変数、`varexternal`を参照）に対して。
  * `ϵ_target`: 最終的なターゲット距離（または一般的には、ABCカーネルのターゲット幅）；`ϵ_target`または`nsims_max`に達した場合、アルゴリズムは停止します。
  * `varexternal`: `dist!`に対する第二の位置引数として渡され、スレッドセーフな方法で距離計算を迅速に行うために使用できる外部変数；`varexternal`内のオブジェクトは、`parallel`モードでもインプレースで変更可能であり、各スレッドは`varexternal`の独自のコピーを受け取ります（必要ない場合は`nothing`を入力）。
  * `nparticles::Int=100`: 推論に使用する総粒子数。
  * `α=0.95`: 逐次ターゲット分布を指定するためのϵの適応的選択に使用される；技術的には、ϵは現在の粒子距離の`α`-分位点になります。
  * `δess=0.5`: 有効サンプルサイズの割合が`δess`を下回ると、層化再サンプリングステップが実行されます。
  * `nsims_max::Int=10^7`: `dist!`評価の最大数（事前からの初期サンプルはカウントしない）；`ϵ_target`または`nsims_max`に達した場合、アルゴリズムは停止します。
  * `Kmcmc::Int=3`: 現在のϵとABCカーネルタイプによって指定された各逐次ターゲット分布でのMCMC（マルコフ連鎖モンテカルロ）ステップの数；実際の数は、`Kmcmc_min`によって指定された早期終了により少なくなる可能性があります。
  * `Kmcmc_min=1.0`: 生存している粒子ごとの受け入れの累積最小値；この値に早期に達した場合（総`Kmcmc` MCMCステップを完了する前に）、ループは早期に終了します；各ϵターゲットで正確に`Kmcmc` MCMCステップを計算するには、`Kmcmc_min=Inf`を設定します。
  * `ABCk=ABCdeZ.Indicator0toϵ`: 距離値を受け取るϵ幅によって指定されるABCカーネル。
  * `facc_min=0.15`: 受け入れられたMCMC提案の割合が`facc_min`を下回ると、差分進化提案は`facc_tune`の因子で減少します。
  * `facc_tune=0.975`: MCMCステップでの差分進化提案のジャンプ距離を減少させる因子（`facc_min`に達した場合に使用）。
  * `verbose::Bool=true`: `true`に設定すると、冗長性が有効になります（REPLへの出力）。
  * `verboseout::Bool=true`: `true`に設定すると、アルゴリズムはより詳細な推論出力を返します。
  * `rng=Random.GLOBAL_RNG`: 推論に使用されるAbstractRNGオブジェクト。
  * `parallel::Bool=false`: `true`に設定すると、スレッド並列性が有効になります；この場合、`dist!`はスレッドセーフである必要があります（例：`varexternal`を利用する）。

# 例

```julia-repl
julia> using ABCdeZ, Distributions;
julia> data = 5;
julia> prior = Normal(0, sqrt(10));
julia> model(θ) = rand(Normal(θ, 1));
julia> dist!(θ, ve) = abs(model(θ)-data), nothing;
julia> ϵ = 0.3;
julia> r = abcdesmc!(prior, dist!, ϵ, nothing, nparticles=1000, parallel=true);
julia> posterior = [t[1] for t in r.P[r.Wns .> 0.0]];
julia> evidence = exp(r.logZ);
```
