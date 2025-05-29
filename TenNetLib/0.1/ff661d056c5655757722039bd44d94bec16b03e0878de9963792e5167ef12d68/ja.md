```
function moveisometry_to_next!(ttn::TTN, node1::Int2, node2::Int2; kwargs...)
```

TTNの同相性/直交中心を`node1::Int2`から隣接する`node2::Int`に移動します。`node1`と`node2`は隣接ノードでなければなりません。`node1`は直交中心でなければならず、`ignore_orthocenter = true`でない限りそうでなければなりません。

**注意**: その後、TTNを正規化しません。

#### 名前付き引数とそのデフォルト値。

  * `ignore_orthocenter::Bool` = false: `true`に設定されている場合、`node1`は直交中心である必要はありません。
  * `maxdim::Int = typemax(Int)`: SVD切り捨て後の最大ボンド次元。
  * `mindim::Int = 1`: SVD切り捨て後の最小ボンド次元。
  * `cutoff::Float64 = Float64_threshold()`: SVD切り捨てのカットオフ。
  * `svd_alg::String = "divide_and_conquer"`.
