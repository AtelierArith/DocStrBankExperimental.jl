```
make_regression(n, p; kwargs...)
```

ガウス入力特徴とガウスノイズを伴う線形応答を生成し、回帰モデルで使用します。

### 戻り値

デフォルトでは、テーブル `X` が `p` 列と `n` 行（観測値）を持つタプル `(X, y)` を返し、対応する `n` の `Continuous` ターゲット観測値 `y` のベクトルが返されます。

### キーワード

  * `intercept=true`: 切片のあるモデルからデータを生成するかどうか。
  * `n_targets=1`: ターゲットの列数。
  * `sparse=0`: 生成する重みベクトルのスパースな割合。
  * `noise=0.1`: 応答（ターゲット）に追加されるガウスノイズの標準偏差。
  * `outliers=0`: 高い分散を持つランダムな量を追加することで外れ値として扱う応答ベクトルの割合。（`binary` が `false` の場合のみ適用されます。）
  * `as_table=true`: `X`（および `n_targets > 1` の場合の `y`）をテーブルまたは行列として返すかどうか。
  * `eltype=Float64`: `X` と `y` の要素型。`AbstractFloat` のサブタイプでなければなりません。
  * `binary=false`: ターゲットをバイナライズするかどうか（シグモイドを介して）。
  * `eltype=Float64`: ポイントの機械型（`AbstractFloat` の任意のサブタイプ）。
  * `rng=Random.GLOBAL_RNG`: 任意の `AbstractRNG` オブジェクト、または `MersenneTwister` をシードする整数（再現性のため）。
  * `as_table=true`: ポイントをテーブル（true）または行列（false）として返すかどうか。

### 例

```julia
X, y = make_regression(100, 5; noise=0.5, sparse=0.2, outliers=0.1)
```
