```
(e_bwd,theta)=compute_bwd_theta(;
    bnd_rel_err = compute_bnd_rel_bwd_err(:exp, graph),
    tolerance = eps(coefftype) / 2,
    theta_init = big"0.2",
    use_log = false,
)

(e_bwd,theta)=compute_bwd_theta(
    graph::Compgraph{T};
    coefftype = T,
    numterms = 100,
    numdigits = 100,
    tolerance = eps(coefftype) / 2,
    theta_init = big"0.2",
    use_log = false,
)
```

相対後方誤差の上限を対応するθで計算します。

最初の出力 $e_{bwd}$ は、計算グラフ `graph` の基礎となる多項式の相対後方誤差の上限を返す関数です。これは指数関数の近似として見なされます。基礎となる多項式 $p$ に対して、この関数は `|δ|` の上限を返します。ここで `δ` は exp(z+δ) = p(z) を満たすものです。この関数は `compute_bnd_rel_bwd_err(:graph)` を使用して計算されます。

2番目の出力 $θ$ は、$e_{bwd}(θ) ≤ tolerance$ となる最大の正の実数です。ここで $tolerance$ はデフォルトでデータ型 `coefftype` の単位丸め誤差であり、これは `graph` の係数の型にデフォルトで設定されます。

$$
theta
$$

の値は、方程式 $e_{bwd}(z) = tolerance$ を近似的に解くことによって推定されます。これは、初期値を `theta_init` に設定した組み込み関数 `fzero` を使用します。デフォルトでは、この根探索手法は高精度算術を使用します。

kwarg `use_log` が `true` に設定されている場合、$theta$ の値は方程式 $log(e_{bwd}(z)) = log(tolerance)$ の解を近似することによって計算されます。

代替形式は、相対後方誤差の上限を返す関数を受け入れます。デフォルトでは、この関数は `compute_bnd_rel_bwd_err(:exp, ...)` で構築され、最初の形式の kwarg のデフォルト値が使用されます。
