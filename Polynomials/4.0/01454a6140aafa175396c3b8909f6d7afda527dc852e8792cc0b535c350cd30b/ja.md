```
fit(P::Type{<:StandardBasisPolynomial}, x, y, J, [cs::Dict{Int, T}]; weights, var)
```

制約付き最小二乗法を使用して、`p = ∑_{i ∈ J} aᵢ xⁱ + ∑ cⱼxʲ` の形の多項式をフィットさせます。ここで、`cⱼ` は固定された非ゼロ定数です。

  * `J`: 係数を見つけるための次数のコレクション
  * `cs`: 指定された場合、固定された非ゼロ定数の次数と値を示す `Dict`、`i => cᵢ`。

`cs` の次数と `J` の次数は交差してはいけません。

例

```julia
x = range(0, pi/2, 10)
y = sin.(x)
P = Polynomial
p0 = fit(P, x, y, 5)
p1 = fit(P, x, y, 1:2:5)
p2 = fit(P, x, y, 3:2:5, Dict(1 => 1))
[norm(p.(x) - y) for p ∈ (p0, p1, p2)] # 1.7e-5, 0.00016, 0.000248
```
