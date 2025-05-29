```
function isometrize!(ttn::TTN, node::Int2; kwargs...)
```

TTNの同型性/直交性の中心を新しい中心`node`に移動します。TTNに適切な直交性の中心がない場合、TTNを最初から同型化します。

#### 名前付き引数とそのデフォルト値。

  * `normalize::Bool = true`: 同型化後にTTNを正規化するかどうか。
  * `maxdim::Int = typemax(Int)`: SVD切り捨て後の最大ボンド次元。
  * `mindim::Int = 1`: SVD切り捨て後の最小ボンド次元。
  * `cutoff::Float64 = Float64_threshold()`: SVD切り捨てのカットオフ。
  * `svd_alg::String = "divide_and_conquer"`.
