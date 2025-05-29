```
xgboost(data; num_round=10, watchlist=Dict(), kw...)
xgboost(data, ℓ′, ℓ″; kw...)
```

トレーニングデータ `data` に対して xgboost グラデーションブースターオブジェクトを作成し、`nrounds` のトレーニングを実行します。これは本質的に、`data` とキーワード引数を使って [`Booster`](@ref) を構築し、その後に [`update!`](@ref) を `nrounds` 回実行するためのエイリアスです。

`watchlist` は、キーが監視するデータの名前を示す文字列で、値がデータを含む [`DMatrix`](@ref) オブジェクトである辞書です。早期*停止*ラウンドを利用する場合、`watchlist` に要素が 1 つ以上あるときは、OrderedDict を使用することが必須です。これにより、XGBoost が早期停止を行うために正しい意図されたデータセットを使用します。

`early_stopping_rounds` は、0 より大きい値に設定されている場合、早期停止を有効にします。検証メトリックは、k ラウンドごとに少なくとも 1 回は改善する必要があります。`watchlist` が明示的に提供されていない場合、トレーニングデータセットを使用して停止基準を評価します。それ以外の場合、`watchlist` の最後のデータ要素と `eval_metric` の最後のメトリック（複数ある場合）を使用します。`early_stopping_rounds` が有効な場合、`watchlist` は空であってはならないことに注意してください。

`maximize` 早期*停止*ラウンドが設定されている場合、このパラメータも設定する必要があります。false の場合、評価スコアが小さいほど良いことを意味します。true に設定すると、評価スコアが大きいほど良いことを意味します。

他のすべてのキーワード引数は [`Booster`](@ref) に渡されます。いくつかの例外を除いて、これらはモデルトレーニングのハイパーパラメータです。包括的なリストについては [こちら](https://xgboost.readthedocs.io/en/stable/parameter.html) を参照してください。

カスタム損失関数は、その1階および2階導関数（それぞれ `ℓ′` と `ℓ″`）を介して提供できます。詳細については [`updateone!`](@ref) を参照してください。

## 例

```julia
# 例 1: XGBoost の基本的な使用法
(X, y) = (randn(100,3), randn(100))

b = xgboost((X, y), num_round=10, max_depth=10, η=0.1)

ŷ = predict(b, X)

# 例 2: ウォッチリストを使用した早期停止（検証セットを使用）
dtrain = DMatrix((randn(100,3), randn(100)))
dvalid = DMatrix((randn(100,3), randn(100)))

watchlist = OrderedDict(["train" => dtrain, "valid" => dvalid])

b = xgboost(dtrain, num_round=10, early_stopping_rounds = 2, watchlist = watchlist, max_depth=10, η=0.1)

# predict 関数の ntree_limit は、XGBoost API 1.4+ の iteration_range の上限を設定するのに役立ちます
ŷ = predict(b, dvalid, ntree_limit = b.best_iteration)
```
