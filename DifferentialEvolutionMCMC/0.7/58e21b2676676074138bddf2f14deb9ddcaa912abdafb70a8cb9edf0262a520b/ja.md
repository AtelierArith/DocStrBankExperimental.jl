```
function DE(;
    n_groups = 4, 
    priors = nothing, 
    Np, 
    burnin = 1000, 
    discard_burnin = true, 
    α = .1,
    β = .1, 
    ϵ = .001,
    σ = .05, 
    κ = 1.0, 
    θsnooker = 0.0, 
    bounds, 
    n_initial = 0, 
    generate_proposal = random_gamma, 
    update_particle! = mh_update!,
    evaluate_fitness! = compute_posterior!, 
    sample = sample,
    blocking_on = x -> false,
    blocks = [false])
```

微分進化MCMCオブジェクト。

# キーワード

  * `n_groups=4`: 粒子のグループ数。
  * `Np`: グループごとの粒子数。
  * `burnin=1000`: バーンイン反復の数。
  * `discard_burnin`: バーンインサンプルが破棄されるかどうかを示します。デフォルトはtrueです。
  * `α=.1`: 移動確率。
  * `β=.1`: 突然変異確率。
  * `ϵ=.001`: クロスオーバーステップのノイズ。
  * `σ=.05`: 突然変異のためにパラメータに追加されるノイズの標準偏差。
  * `κ=1.0`: クロスオーバー中の確率(1-κ)での再結合。
  * `θsnooker=0`: 線x_i - zに沿ってサンプルします。0.1は0より大きい場合に推奨されます。
  * `n_initial`: `sample=resample`のときの事前分布からの初期サンプル数。パラメータの数の10倍が典型的な値です。
  * `bounds`: 各パラメータの下限と上限のタプルのベクトル。
  * `iter`: 現在の反復。
  * `generate_proposal`: 提案を生成する関数。デフォルトはTurner et al. 2012で説明されている2モード提案です。`fixed_gamma`、`variable_gamma`（ヘルプを参照）を選択するか、カスタム関数を渡すこともできます。
  * `update_particle!`: 提案値で粒子を更新するための関数。デフォルト: `mh_update!`、これはメトロポリス-ヘイスティングスルールを使用します。
  * `evaluate_fitness!`: 事後のフィットネスを評価するための関数。デフォルトは`compute_posterior!`を使用して事後の対数尤度を計算します。最適化のためには`evaluate_fun!`を選択します。
  * `sample`: クロスオーバーステップ中に粒子をサンプリングするための関数。デフォルトの`sample`は現在の粒子パラメータ値を使用しますが、`resample`は各粒子の受け入れられた値の履歴からサンプリングします。`resample`を使用する場合、Npは3以上でなければなりません。
  * `blocking_on = x -> false`: 各反復でブロック更新が使用されているかどうかを示す関数。この関数はDEサンプラーオブジェクトのためのoptimization_tests引数を必要とし、真または偽の値を返さなければなりません。
  * `blocks`: 更新するパラメータを示すブールベクトルのベクトル。各サブベクトルはブロックを表し、サブベクトル内の各要素はブロック内で更新されるパラメータを示します。例えば、[[true,false],[false,true]]は、最初のブロックで最初の位置のパラメータが更新され、2番目のブロックで2番目の位置のパラメータが更新されることを示します。パラメータがベクトルまたは行列である場合、それらはブロックサブベクトル内にネストされます。

# 参考文献

  * Ter Braak, C. J. A Markov Chain Monte Carlo version of the genetic algorithm Differential Evolution: easy Bayesian computing for real parameter spaces.
  * Ter Braak, Cajo JF, and Jasper A. Vrugt. Differential evolution Markov chain with snooker updater and fewer chains. Statistics and Computing 18.4 (2008): 435-446
  * Turner, B. M., Sederberg, P. B., Brown, S. D., & Steyvers, M. (2013). A method for efficiently sampling from distributions with correlated dimensions. Psychological methods, 18(3), 368.
  * Turner, B. M., & Sederberg, P. B. (2012). Approximate Bayesian computation with differential evolution. Journal of Mathematical Psychology, 56(5), 375-385.
