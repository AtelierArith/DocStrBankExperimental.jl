```
ProdCVI
```

`ProdCVI` 構造体は、`prod(approximation::CVI, logp::F, dist)` の近似手法のハイパーパラメータを定義します。このメソッドは、確率分布 `dist` と `logp` の積の近似を確率的変分メッセージパッシング (SVMP-CVI) を用いて行います (詳細は [`確率的変分メッセージパッシングによる確率プログラミング`](https://biaslab.github.io/publication/probabilistic_programming_with_stochastic_variational_message_passing/) を参照)。

!!! note
    `ProdCVI` は `CVIProjection` に取って代わられました。


引数

  * `rng`: ランダム数生成器
  * `n_samples`: 統計近似に使用するサンプル数
  * `n_iterations`: 自然パラメータの勾配最適化のための反復回数
  * `opt`: 自然パラメータの勾配最適化ステップを実行するために使用されるオプティマイザ
  * `grad`: オプション、デフォルトは `ForwardDiffGrad()`、勾配とヘッセ行列の計算方法を選択するための構造体
  * `n_gradpoints`: オプション、デフォルトは 1、尤度 (dist*logp) の勾配を推定するためのポイント数
  * `enforce_proper_messages`: オプション、デフォルトは true、入力エッジに向けて計算されたメッセージが適切な分布であることを保証し、`Val(true)/Val(false)` 型でなければなりません
  * `warn`: オプション、デフォルトは true、最適化ステップに関連する警告を有効または無効にします

!!! note
    ガウスの場合、`n_gradpoints` オプションは無視されます


!!! note
    Julia 環境に `Optimisers.jl` を追加すると、CVI 近似手法のための追加のオプティマイザが利用可能になります。すべての入力が `Gaussian` 型である場合、Julia 環境に `DiffResults` を追加すると、より高速な勾配計算が可能になります。

