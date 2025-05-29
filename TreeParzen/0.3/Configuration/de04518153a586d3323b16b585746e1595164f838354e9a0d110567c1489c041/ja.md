```julia
struct Config
```

  * `threshold::Float64`
  * `linear_forgetting::Int64`
  * `draws::Int64`
  * `random_trials::Int64`
  * `prior_weight::Float64`
  * `threshold` : `0` と `1` の間の値で、期待される改善基準がモデル化される確率の閾値を制御します。
  * `linear_forgetting` : 確率モデルに使用される履歴ポイントの数を制御する正の値で、これを超える古いポイントは線形的に重み付けが減少します。
  * `draws` : 次の最適化候補の推奨を行う際に引き出すサンプルの数を制御する正の値です。
  * `random_trials` : TreeParzen最適化が使用される前に、ランダムに生成された候補ポイントの試行回数を制御する正の値です。
  * `prior_weight` : `0` と `1` の間の値で、ユーザー指定の確率パラメータの重要性と試行の履歴とのバランスを制御します。
