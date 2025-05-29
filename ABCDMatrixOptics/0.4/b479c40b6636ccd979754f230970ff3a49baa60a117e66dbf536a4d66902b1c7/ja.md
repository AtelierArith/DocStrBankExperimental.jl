```
GaussianBeam(q; zpos, n=1.0, λ=633e-9)
```

複素ビームパラメータ `q` によって定義される `GaussianBeam` を返します。

## 例

```jldoctest
julia> GaussianBeam(12 + 1im * 1.0 * π * 100e-6^2 / 633e-9)
GaussianBeam{Float64}(12.0 + 0.049630215696521214im, 0.0, 1.0, 6.33e-7)
```
