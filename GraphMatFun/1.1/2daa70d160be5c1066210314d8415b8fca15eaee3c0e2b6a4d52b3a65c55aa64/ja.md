```
(e_fwd,theta)=compute_fwd_theta(
    graph::Compgraph{T},
    f;
    coefftype = T,
    tolerance = eps(coefftype) / 2,
    theta_init = big"0.1",
)
```

`f`の近似に対する相対前方誤差と対応するθを返します。

最初の出力 $e_{fwd}$ は、相対前方誤差を計算する関数であり、$e_{fwd}(z)=|f(z) - p(z)| / |z|$ です。ここで、$p$ は計算グラフ `graph` の基になる多項式です。これは、$p$ が何らかの意味で $f$ を近似する場合にのみ意味があります。

2番目の出力 $θ$ は、$e_{fwd}(θ) ≤ tolerance$ となる最大の正の実数であり、ここで $tolerance$ はデフォルトでデータ型 `coefftype` の単位丸め誤差であり、これはさらに `graph` の係数の型にデフォルトします。

$$
θ
$$

の値は、初期値を `theta_init` に設定して組み込み関数 `fzero` を使用して近似されます。デフォルトでは、この根探索手法は高精度算術を使用します。
