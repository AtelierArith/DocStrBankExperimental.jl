```
(model::CovGaussianNetwork)(rng::AbstractRNG, state::AbstractArray{<:Any, 3}; is_sampling::Bool=false, is_return_log_prob::Bool=false)
```

この関数は多次元アクション空間に対応しています。共分散行列を扱うために、出力は3Dテンソルです。サンプリングを行う場合、次元が`(action_size x action_samples x batchsize)`のアクションテンソルと、次元が`(1 x action_samples x batchsize)`の`logp_π`テンソルを返します。サンプリングを行わない場合、次元が`(action_size x 1 x batchsize)`の`μ`と、共分散行列のコレスキー分解の下三角行列`L`（次元は`(action_size x action_size x batchsize)`）を返します。共分散行列は、`Σ = stack(map(l -> l*l', eachslice(L, dims=3)); dims=3)`を使用して取得できます。

  * `rng::AbstractRNG=Random.default_rng()`
  * `is_sampling::Bool=false`、得られた正規分布からサンプリングするかどうか。
  * `is_return_log_prob::Bool=false`、与えられた状態でアクションを得る条件付き確率を計算するかどうか。

```
