```
crossprediction(source_train, target_train, source_pred,
                em::AbstractSpatialEmbedding; kwargs...)
```

`source` から `target` への時空間時系列クロス予測を行います。これは、局所加重モデリング [1] を使用します。これは、結合された空間フィールドがあり、一方が他方を予測するために使用される場合に使用できます。`source_train`、`target_train`、`source_pred` はすべて同じ型、`AbstractVector{<:AbstractArray{T, Φ}}` であると仮定します。

時空間遅延埋め込みプロセスは `em` によって定義されます。利用可能なメソッドとインターフェースについては [`AbstractSpatialEmbedding`](@ref) を参照してください。

## キーワード引数

  * `ttype = KDTree` : ツリー構造の型/コンストラクタ。これまでのところ、`KDTree` でのみテストされています。
  * `method = AverageLocalModel(ω_safe)` : [`AbstractLocalModel`](@ref) のサブタイプ。
  * `ntype = FixedMassNeighborhood(3)` : `AbstractNeighborhood` のサブタイプ。
  * `progress = true` : 進捗を表示するため。

## 説明

再構成された状態 `source_train[t][i,j,...]` は出力値 `target_train[t][i,j,...]` に関連付けられています。これにより、`target` と `source` の間に「接続」が確立されます。`source_pred` の再構成された状態をクエリポイントとして取り、関数は近隣 `ntype` を使用して `source_train` の再構成空間内の近隣を見つけます。次に、近隣の *インデックス* を使用して、フィールド間の確立された「接続」を使用して `target` の対応する値の予測を行います。

## 追加インターフェース

同じトレーニングセットと埋め込みパラメータで繰り返し予測を行う場合の計算時間を節約するために、ユーザーが既存の再構成とツリー構造を提供できる追加インターフェースを提供します。

```julia
R = reconstruct(train_in, em)
tree = ttype(R)
params = PredictionParams(em, method, ntype, ttype)
sol = crossprediction(params, train_out, pred_in, R, tree; progress=true)
```

ここで、`params` はすべての関連パラメータを含む内部コンテナです。

## パフォーマンスノート

埋め込みパラメータを選択する際は注意が必要です。メモリ使用量と計算時間は、結果として得られる埋め込み次元に強く依存します。

## 参考文献

[1] : U. Parlitz & C. Merkwirth, [Phys. Rev. Lett. **84**, pp 1890 (2000)](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.84.1890)
