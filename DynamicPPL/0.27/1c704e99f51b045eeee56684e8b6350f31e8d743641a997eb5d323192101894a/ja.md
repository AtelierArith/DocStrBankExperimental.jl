```
generated_quantities(model::Model, chain::AbstractChains)
```

`chain`の各サンプルに対して`model`を実行し、各サンプルに対して`model`が返す値の配列を返します。

# 例

## 一般

モデル内で計算された追加の量を検査したい場合がよくあります。例えば：

```julia
@model function demo(x)
    # サンプリングと観察
    θ ~ Prior()
    x ~ Likelihood()
    return interesting_quantity(θ, x)
end
m = demo(data)
chain = sample(m, alg, n)
# `θ`が事後分布/`chain`からのサンプルに置き換えられた`interesting_quantity(θ, x)`を検査するために：
generated_quantities(m, chain) # <= `interesting_quantity(θ, x)`から返された値の`Vector`が得られます
```

## 具体的（かつシンプル）

```julia
julia> using DynamicPPL, Turing

julia> @model function demo(xs)
           s ~ InverseGamma(2, 3)
           m_shifted ~ Normal(10, √s)
           m = m_shifted - 10

           for i in eachindex(xs)
               xs[i] ~ Normal(m, √s)
           end

           return (m, )
       end
demo (generic function with 1 method)

julia> model = demo(randn(10));

julia> chain = sample(model, MH(), 10);

julia> generated_quantities(model, chain)
10×1 Array{Tuple{Float64},2}:
 (2.1964758025119338,)
 (2.1964758025119338,)
 (0.09270081916291417,)
 (0.09270081916291417,)
 (0.09270081916291417,)
 (0.09270081916291417,)
 (0.09270081916291417,)
 (0.043088571494005024,)
 (-0.16489786710222099,)
 (-0.16489786710222099,)
```
