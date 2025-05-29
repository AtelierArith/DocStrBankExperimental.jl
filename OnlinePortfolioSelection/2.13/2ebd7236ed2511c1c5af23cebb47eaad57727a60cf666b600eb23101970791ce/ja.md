```
EGA{T<:AbstractFloat}<:EGMFramework
```

EGMアルゴリズムのEGAバリアント。

# フィールド

  * `gamma1::T`: モーメンタムパラメータ
  * `gamma2::T`: モーメンタムパラメータ

# 例

```julia
julia> model = EGA(0.99, 0.)
EGA{Float64}(0.99, 0.0)
```
