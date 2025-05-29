```julia
MarchenkoPastur <:ContinuousUnivariateDistribution

MarchenkoPastur(λ,σ) 
pdf(d::MarchenkoPastur,x::Real)  
```

  * `λ` : default `0.5`
  * `σ` : default `1`

# Examples

Generate a MP rv with ρ = 0.5, σ = 1

```julia
rand(MarchenkoPastur())

1.2656480923753979
```

Compute the desity for the MP distribution with λ=1.6 at the point 0

```julia
pdf(MarchenkoPastur(1.6),0)

0.375
```

Generate 100 MP rvs with ρ=0.1 and σ = 2

```julia
rand(MarchenkoPastur(0.1,2),100)

100-element Vector{Float64}:
 5.31001367107032
 2.3707745658317116
 2.5378523986772343
 2.585256212138476
 ⋮
 3.66799182506567
 6.517865226831382
 3.7628212250212423
 4.582520400697299
```
