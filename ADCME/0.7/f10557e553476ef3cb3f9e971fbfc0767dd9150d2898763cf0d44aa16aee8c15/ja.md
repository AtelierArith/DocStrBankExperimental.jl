```
ae(x::Union{Array{Float64}, PyObject}, output_dims::Array{Int64}, θ::Union{Array{Float64}, PyObject};
activation::Union{Function,String, Nothing} = "tanh")
```

エイリアス: `fc`, `ae`

中間のニューロン数 `output_dims` を持つニューラルネットワークを作成します。重みは `θ` によって与えられます。

# 例 1: 重みとバイアスを明示的に構築する

```julia
x = constant(rand(10,2))
n = ae_num([2,20,20,20,2])
θ = Variable(randn(n)*0.001)
y = ae(x, [20,20,20,2], θ)
```

# 例 2: 重みとバイアスを暗黙的に構築する

```julia
θ = ae_init([10,20,20,20,2]) 
x = constant(rand(10,10))
y = ae(x, [20,20,20,2], θ)
```

他にも [`ae_num`](@ref), [`ae_init`](@ref) を参照してください。
