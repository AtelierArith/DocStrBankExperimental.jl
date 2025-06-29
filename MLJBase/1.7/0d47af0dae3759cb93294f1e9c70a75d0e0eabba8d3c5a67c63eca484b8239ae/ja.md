```
make_moons(n::Int=100; kwargs...)
```

ラベル付きの二次元ポイントを生成し、2つの交差した半円に近い位置に配置します。分類およびクラスタリングモデルで使用します。

### 戻り値

デフォルトでは、`n` 行（観測値）と `2` 列を持つテーブル `X` と、対応する `n` の `Multiclass` ターゲット観測値 `y` のベクトルが返されます。ターゲットは `0` または `1` で、左または右の半円への所属を示します。

### キーワード引数

  * `shuffle=true`: 結果のポイントをシャッフルするかどうか、
  * `noise=0.1`: データに追加されるガウスノイズの標準偏差、
  * `xshift=1.0`: 最初の中心に対する2番目の中心の水平方向の移動量。
  * `yshift=0.3`: 最初の中心に対する2番目の中心の垂直方向の移動量。
  * `eltype=Float64`: ポイントの機械タイプ（`AbstractFloat` の任意のサブタイプ）。
  * `rng=Random.GLOBAL_RNG`: 任意の `AbstractRNG` オブジェクト、または `MersenneTwister` をシードするための整数（再現性のため）。
  * `as_table=true`: ポイントをテーブル（true）または行列（false）として返すかどうか。`false` の場合、ターゲット `y` は整数要素型になります。

### 例

```julia
X, y = make_moons(100; noise=0.5)
```
