```julia
calcProductGaussians(
    M,
    kernels;
    μ0,
    weight,
    do_transport_correction
)

```

実験的: マンフォールド上のガウスの積。

開発ノート

  * FIXME リー群上の集中ガウスの積を行う（近似）:

      * [Ge, van Goor, Mahony: A Geometric Perspective on using Gaussian Distributions on Lie Groups, 2024]のセクション3.2および4を参照してください。
      * また、上流のユーティリティも参照してください、https://juliamanifolds.github.io/Manifolds.jl/stable/features/distributions.html
  * FIXME 異なる接空間からの共分散と掛け算する際に平行輸送は必要か？
