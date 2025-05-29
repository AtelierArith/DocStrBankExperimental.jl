```
AnisotropicExponential(A, [σ = 1])
```

異方性指数共分散構造で、異方性行列 `A` と（オプションの）周辺標準偏差 `σ` を持ち、次のように定義されます。

$$
C(x, y) = \exp(-ρᵀ A ρ)
$$

ここで $ρ = x - y$ です。

# 例

```jldoctest
julia> A = [1 0.5; 0.5 1];

julia> AnisotropicExponential(A)
anisotropic exponential (A=[1.0 0.5; 0.5 1.0], σ=1.0)

```
