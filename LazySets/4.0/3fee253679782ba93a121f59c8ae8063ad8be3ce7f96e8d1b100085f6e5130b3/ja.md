```
ρ(d::AbstractVector, em::ExponentialMap;
  [backend]=get_exponential_backend())
```

指数写の支持関数を評価します。

### 入力

  * `d`       – 方向
  * `em`      – 指数写
  * `backend` – （オプション; デフォルト: `get_exponential_backend()`）指数化バックエンド

### 出力

指定された方向における支持関数の評価。

### 注意事項

もし $E = \exp(M)⋅X$ であり、$M$ が行列、$X$ が集合であるなら、任意の方向 $d$ に対して $ρ(d, E) = ρ(\exp(M)^T d, X)$ が成り立ちます。
