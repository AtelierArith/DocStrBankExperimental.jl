```
function position!(sysenv::StateEnvsTTN, node::Int2;
                   maxdim::Int = typemax(Int),
                   mindim::Int = 1,
                   cutoff::Float64 = Float64_threshold(),
                   svd_alg::String = "divide_and_conquer",
                   normalize::Bool = true)
```

`TTN`の直交中心を`node`に移動し、同じ有効ハミルトニアンを更新します。

#### 名前付き引数とそのデフォルト値:

  * `normalize::Bool = true`: 後で正規化するかどうか。
  * `maxdim::Int = typemax(Int)`: SVD切り捨て後の最大ボンド次元。
  * `mindim::Int = 1`: SVD切り捨て後の最小ボンド次元。
  * `cutoff::Float64 = Float64_threshold()`: SVD切り捨てのカットオフ。
  * `svd_alg::String = "divide_and_conquer"`.
