```
For(f, base...)
```

`For`は`ProductMeasure`を構築するための便利な方法を提供します。`base`にはいくつかのオプションがあります。Juliaの`do`構文を使用すると、標準の`for`ループに非常に似た形に見えますが、作業しやすい意味論的構造を維持します。

---

# `For(f, base::Int...)`

`base`に1つまたは複数の`Int`値が渡されると、結果は`CartesianIndices(base)`に依存するものとして扱われます。

```
julia> For(3) do λ Exponential(λ) end |> marginals
3-element mappedarray(MeasureBase.var"#17#18"{var"#15#16"}(var"#15#16"()), ::CartesianIndices{1, Tuple{Base.OneTo{Int64}}}) with eltype Exponential{(:λ,), Tuple{Int64}}:
 Exponential(λ = 1,)
 Exponential(λ = 2,)
 Exponential(λ = 3,)
```

```
julia> For(4,3) do μ,σ Normal(μ,σ) end |> marginals
4×3 mappedarray(MeasureBase.var"#17#18"{var"#11#12"}(var"#11#12"()), ::CartesianIndices{2, Tuple{Base.OneTo{Int64}, Base.OneTo{Int64}}}) with eltype Normal{(:μ, :σ), Tuple{Int64, Int64}}:
 Normal(μ = 1, σ = 1)  Normal(μ = 1, σ = 2)  Normal(μ = 1, σ = 3)
 Normal(μ = 2, σ = 1)  Normal(μ = 2, σ = 2)  Normal(μ = 2, σ = 3)
 Normal(μ = 3, σ = 1)  Normal(μ = 3, σ = 2)  Normal(μ = 3, σ = 3)
 Normal(μ = 4, σ = 1)  Normal(μ = 4, σ = 2)  Normal(μ = 4, σ = 3)
```

---

# `For(f, base::AbstractArray...)``

この場合、`base`は配列が`zip`されてからマップが適用されるかのように振る舞います。

```
julia> For(randn(3)) do x Exponential(x) end |> marginals
3-element mappedarray(x->Main.Exponential(x), ::Vector{Float64}) with eltype Exponential{(:λ,), Tuple{Float64}}:
 Exponential(λ = -0.268256,)
 Exponential(λ = 1.53044,)
 Exponential(λ = -1.08839,)
```

```
julia> For(1:3, 1:3) do μ,σ Normal(μ,σ) end |> marginals
3-element mappedarray((:μ, :σ)->Main.Normal(μ, σ), ::UnitRange{Int64}, ::UnitRange{Int64}) with eltype Normal{(:μ, :σ), Tuple{Int64, Int64}}:
 Normal(μ = 1, σ = 1)
 Normal(μ = 2, σ = 2)
 Normal(μ = 3, σ = 3)
```

---

# `For(f, base::Base.Generator)`

`Generator`の場合、関数はジェネレーターの値に対してマップされます：

```
julia> For(eachrow(rand(4,2))) do x Normal(x[1], x[2]) end |> marginals |> collect
4-element Vector{Normal{(:μ, :σ), Tuple{Float64, Float64}}}:
 Normal(μ = 0.255024, σ = 0.570142)
 Normal(μ = 0.970706, σ = 0.0776745)
 Normal(μ = 0.731491, σ = 0.505837)
 Normal(μ = 0.563112, σ = 0.98307)
```
