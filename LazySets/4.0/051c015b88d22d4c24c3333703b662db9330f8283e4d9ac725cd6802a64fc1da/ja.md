```
σ(d::AbstractVector, eprojmap::ExponentialProjectionMap;
  [backend]=get_exponential_backend())
```

指数写像の射影のサポートベクトルを返します。

### 入力

  * `d`        – 方向
  * `eprojmap` – 指数写像の射影
  * `backend`  – （オプション; デフォルト: `get_exponential_backend()`）指数化バックエンド

### 出力

指定された方向のサポートベクトル。方向のノルムがゼロの場合、結果はラップされた集合に依存します。

### 注意事項

$$
S = (L⋅M⋅R)⋅X
$$

の場合、ここで $L$ と $R$ は行列、$M$ は行列指数、$X$ は集合であるとき、任意の方向 $d$ に対して $σ(d, S) = L⋅M⋅R⋅σ(R^T⋅M^T⋅L^T⋅d, X)$ が成り立ちます。
