```
hampel(x; spread=mad(x), threshold=2)
```

ハンペル基準を使用して外れ値を特定します。

ベクトル `x` が与えられたとき、要素 xₖ を特定します。

$$
|xₖ - m| > t S,
$$

ここで $m$ は要素の中央値、分散スケール $S$ は関数 `spread` によって提供され、パラメータ $t$ は `threshold` によって与えられます。戻り値は `Bool` ベクトルです。

デフォルトでは、`spread` は `mad` で、`threshold` は 2 です。
