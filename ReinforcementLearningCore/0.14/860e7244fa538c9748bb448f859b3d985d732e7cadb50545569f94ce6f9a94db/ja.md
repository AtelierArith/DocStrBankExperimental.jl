```
CategoricalNetwork(model)([rng,] state::AbstractArray [, mask::AbstractArray{Bool}]; is_sampling::Bool=false, is_return_log_prob::Bool = false)
```

CategoricalNetworkは、`state`入力を受け取り、カテゴリカル分布のロジットを出力するモデル（通常はニューラルネットワーク）をラップします。オプションの引数`mask`は、`state`と同じサイズの`Bool`のArrayでなければならず、最初の次元はアクションベクトルの長さでなければなりません。マスクによって`false`にマッピングされたアクションは、ロジットが`-Inf`であり、サンプリングされる確率がゼロになります。

  * `rng::AbstractRNG=Random.default_rng()`
  * `is_sampling::Bool=false`、取得した通常のカテゴリカル分布からサンプリングするかどうか（Flux.OneHotArray `z`を返します）。
  * `is_return_log_prob::Bool=false`、与えられた状態でサンプリングされたアクションを取得するための*ロジット*（すなわち、正規化されていない対数確率）を返すかどうか。

`is_sampling`がtrueの場合にのみ適用され、`z, logits`を返します。

`is_sampling = false`の場合、`model`への単純なフォワードパスによって得られたロジットのみを返します。
