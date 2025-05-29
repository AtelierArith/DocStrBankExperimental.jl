```
rand(M::Segre{ℝ, V}; vector_at=nothing)
```

もし `vector_at` が `nothing` の場合、次の上にランダムな点を返します。

$$
    ℝ^{+} × \mathbb{S}^{n_1 - 1} ×⋯× \mathbb{S}^{n_d - 1}
$$

これは $ℝ^{+}$ 上の対数正規分布と $\mathbb{S}^{n_1 - 1} ×⋯× \mathbb{S}^{n_d - 1}$ 上の一様分布からのものです。

もし `vector_at` が `nothing` でない場合、接空間上の正規分布からランダムな接ベクトルを返します。
