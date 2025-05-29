```
returnTuringParams(model, params; maxiters = 1e3,alg=Rodas5(),abstol=1e-8, reltol=1e-6, tspan=1e4,ensemblealg=EnsembleThreads(),batch_size=1e4)
```

パターン形成が予測されるパラメータの `save_turing` オブジェクトを返します。

必要な入力:

  * `model`: `@reaction_network` マクロを介して指定
  * `params`: `model_parameters` オブジェクト内のすべての反応および拡散パラメータ

オプションの入力:

  * `batch_size`: 一度に考慮するパラメータセットの数。デフォルト値から増減することで速度が改善される場合があります。

DifferentialEquations.jl から引き継がれる入力; 詳細については [こちら](https://docs.sciml.ai/DiffEqDocs/stable/) を参照してください:

  * `maxiters`: 定常状態に達するための最大反復回数（そうでない場合、シミュレーションは終了します）
  * `alg`: ODE ソルバーアルゴリズム
  * `abstol` および `reltol`: ソルバーの許容レベル
  * `tspan`: 定常状態に達するために許可される最大時間（そうでない場合、シミュレーションは終了します）
  * `ensemblealg`: アンサンブルシミュレーションメソッド
