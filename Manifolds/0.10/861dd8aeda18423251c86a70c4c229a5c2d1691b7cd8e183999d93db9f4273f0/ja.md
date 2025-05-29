```
inner(M::Segre{ℝ, V}, p, X, Y,)
```

点$p ≐ (λ, x_1, \dots, x_d)$における二つの接ベクトル$X = (ν, u_1, …, u_d)$と$Y = (ξ, v_1, …, v_d)$の内積。この内積は、ユークリッド計量を備えたテンソルの空間にセグレ多様体を埋め込むことによって得られます：

$$
    \langle X, Y \rangle_{p} = \nu \xi + \lambda^2 (\langle u_1, v_1 \rangle_{x_1} + \dots + \langle u_d, v_d \rangle_{x_d}),
$$

ここで、$ν, ξ ∈ T_{λ} ℝ^{+} = ℝ$であり、$u_i$, $v_i ∈ T_{x_i} \mathbb{S}^{n_i - 1} ⊂ ℝ^{n_i}$です。
