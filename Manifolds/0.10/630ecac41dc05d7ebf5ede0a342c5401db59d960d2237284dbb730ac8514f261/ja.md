```
get_vector(M::Segre{𝔽, V}, p, c, ::DefaultOrthonormalBasis; kwargs...)
```

接触空間 $T_{(λ, x_1,…, x_d)} \mathcal{S}_A = \mathbb{R} × T_{x_1} \mathbb{S}^{n_1 - 1} ×⋯× T_{x_d} \mathbb{S}^{n_d - 1}$ の座標から接ベクトル `X` を取得します。各因子に対して [`DefaultOrthonormalBasis`](@extref `ManifoldsBase.DefaultOrthonormalBasis`) を使用します。
