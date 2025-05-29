```
price!(fin_obj::Option, MonteCarlo{MonteCarloModel}; kwargs...)
```

は、指定されたMonteCarloModelを使用してモンテカルロシミュレーション手法でオプション価格を計算します。注意: モンテカルロ手法で価格を付けられるのはヨーロピアンオプションのみです。

`MonteCarloModel`のタイプ:

  * `LogDiffusion`
  * `MCBootstrap`

# キーワード引数

## LogDiffusionモデルの場合

  * `n_sims`: 実行するシミュレーションの数。デフォルトは100。
  * `sim_size`: 各シミュレーション実行で生成されるステップの数。デフォルトは100。

## MCBootstrapモデルの場合

  * `n_sims`: 実行するシミュレーションの数。デフォルトは100。
  * `bootstrap_method`: 使用するブロックブートストラップ法。`TSBootMethod`のサブタイプでなければなりません。デフォルト=`Stationary`

# 例

```julia
prices = [1,4,3,4,2,5,6,4,7,5];
stock = Stock(prices);
call = EuroCallOption(stock, 8);

price!(call, MonteCarlo{LogDiffusion}; n_sims=50, sim_size=250)
price!(call, MonteCarlo{MCBootstrap}; bootstrap_method=CircularBlock, n_sims=10)
```
