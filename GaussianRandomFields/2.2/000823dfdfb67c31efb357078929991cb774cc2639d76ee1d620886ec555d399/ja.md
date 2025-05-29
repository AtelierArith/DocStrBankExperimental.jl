```
rel_error(grf)
```

ランダムフィールドのカーニュン＝ローヴ近似における相対誤差を返します。これは次のように計算されます。

$$
1 - \displaystyle\frac{\sum \theta_j^2}{\sigma^2 \int_D \mathrm{d}x}
$$

。

長方形の領域で定義されたフィールドにのみ有用です。

# 例

```jldoctest; setup=:(import Random; Random.seed!(12345))
julia> cov = CovarianceFunction(2, Matern(.3, 1))
2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0)

julia> pts = range(0, stop=1, length=51)
0.0:0.02:1.0

julia> grf = GaussianRandomField(cov, KarhunenLoeve(300), pts, pts)
Gaussian random field with 2d Matérn covariance function (λ=0.3, ν=1.0, σ=1.0, p=2.0) on a 51×51 structured grid, using a KL expansion with 300 terms

julia> @printf "%.8f" rel_error(grf)
0.00046071

```
