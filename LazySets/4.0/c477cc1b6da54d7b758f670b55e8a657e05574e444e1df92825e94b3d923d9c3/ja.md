```
σ(d::AbstractVector, em::ExponentialMap;
  [backend]=get_exponential_backend())
```

指数写のサポートベクトルを返します。

### 入力

  * `d`       – 方向
  * `em`      – 指数写
  * `backend` – （オプション; デフォルト: `get_exponential_backend()`）指数化バックエンド

### 出力

指定された方向のサポートベクトル。方向のノルムがゼロの場合、結果はラップされた集合に依存します。

### 注意事項

$$
E = \exp(M)⋅X
$$

の場合、ここで $M$ は行列、$X$ は集合であるとき、任意の方向 $d$ に対して $σ(d, E) = \exp(M)⋅σ(\exp(M)^T d, X)$ が成り立ちます。
