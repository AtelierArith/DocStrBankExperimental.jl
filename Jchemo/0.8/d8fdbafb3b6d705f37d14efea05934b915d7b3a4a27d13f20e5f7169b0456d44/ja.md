```
frob(X)
frob(X, weights::Weight)
frob2(X)
frob2(X, weights::Weight)
```

行列のフロベニウスノルム。

  * `X` : 行列 (n, p)。
  * `weights` : 観測の重み (n)。`Weight` 型のオブジェクト（例えば、関数 `mweight` によって生成される）。

`X` のフロベニウスノルムは：

  * sqrt(tr(X' * X))。

フロベニウス加重ノルムは：

  * sqrt(tr(X' * D * X))、ここで D はベクトル `w` の対角行列。

関数 `frob2` は `frob` の二乗バージョンです。

## 参考文献

@Stevengj,  https://discourse.julialang.org/t/interesting-post-about-simd-dot-product-and-cosine-similarity/123282.
