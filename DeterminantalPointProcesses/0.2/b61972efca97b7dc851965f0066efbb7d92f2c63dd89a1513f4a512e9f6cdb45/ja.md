```
randmcmc([rng::AbstractRNG], kdpp::kDPP, N::Int; kwargs...)
```

k-DPP [2] からの MCMC サンプリング。

## 引数

  * `rng` : 擬似乱数生成器（デフォルトでは Random.GLOBAL_RNG が使用されます）
  * `kdpp` : k-決定論的点過程
  * `N` : サンプル数

## キーワード引数

  * `init_state`
  * `return_final_state`
  * `mix_eps`
  * `mixing_steps`
  * `steps_between_samples`

TODO: 

  * rand と同様に、MCMC を並列で実行するサポートを追加する。
  * 並列化が偏りのない一貫したサンプルを生成することを確認する。
