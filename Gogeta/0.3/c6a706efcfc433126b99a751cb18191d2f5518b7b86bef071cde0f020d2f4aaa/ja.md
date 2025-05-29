```
function optimize_by_walking!(original::JuMP.Model, nn_model::Flux.Chain, U_in, L_in; delta=0.1, return_sampled=false, silent=true, iterations=10, infeasible_per_iter=5)
```

与えられたニューラルネットワークJuMP定式化に対して、完全なリラクシングウォークアルゴリズムを実行します。詳細については、Tong et al. (2024)を参照してください。

# パラメータ

  * `original`: NN定式化を含む`JuMP`モデル。
  * `nn_model`: `Flux.Chain`としての元のNN

# オプションのパラメータ

  * `delta`: バイナリ変数を固定する際に特定のニューロンがどれだけ優先されるかを制御します
  * `return_sampled`: 最適解に加えてサンプリングされたポイントを返します
  * `silent`: コンソールに進捗情報を印刷します
  * `iterations`: 線形リラクゼーションからの新しいスタートの数（バイナリ変数は固定されていない）
  * `infeasible_per_iter`: 次のイテレーションを開始する前に許可される不適合LPリラクゼーションの数
