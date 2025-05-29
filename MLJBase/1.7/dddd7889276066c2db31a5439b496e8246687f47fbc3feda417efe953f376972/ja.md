```
X, y = make_blobs(n=100, p=2; kwargs...)
```

クラスタリングおよび分類問題のためのガウスブロブを生成します。

### 戻り値

デフォルトでは、`p` 列（特徴）と `n` 行（観測）のテーブル `X` と、ブロブのメンバーシップを示す `n` の `Multiclass` ターゲット観測のベクトル `y` が返されます。

### キーワード引数

  * `shuffle=true`: 結果のポイントをシャッフルするかどうか、
  * `centers=3`: センターの数、または `c x p` 行列で、`c` の事前に決定されたセンター、
  * `cluster_std=1.0`: 各ブロブの標準偏差、
  * `center_box=(-10. => 10.)`: センターが提供されていない場合にクラスタセンターが描かれる `p` 次元キューブの制限、
  * `eltype=Float64`: ポイントの機械タイプ（`AbstractFloat` の任意のサブタイプ）。
  * `rng=Random.GLOBAL_RNG`: 任意の `AbstractRNG` オブジェクト、または `MersenneTwister` をシードする整数（再現性のため）。
  * `as_table=true`: ポイントをテーブル（true）または行列（false）として返すかどうか。`false` の場合、ターゲット `y` は整数要素タイプを持ちます。

### 例

```julia
X, y = make_blobs(100, 3; centers=2, cluster_std=[1.0, 3.0])
```
