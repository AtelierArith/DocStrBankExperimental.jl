```
GibbsConditional(sym, conditional)
```

「擬似サンプラー」で、`Gibbs`に解析的なギブス条件を手動で提供します。`GibbsConditional(:x, cond)`は、条件`cond`に従って変数`x`をサンプリングします。したがって、`cond`は条件付き変数の`NamedTuple`から`Distribution`への関数でなければなりません。

渡される`NamedTuple`には、モデルからのすべてのランダム変数が不特定の順序で含まれており、モデルが実行される[`VarInfo`](@ref)オブジェクトから取得されます。スカラーとベクトルはそれぞれの形状で保存されます。このタプルには、条件付き変数自体の値も含まれており、これは便利ですが、これを使用するとギブスサンプラーではなくなります（[こちら](https://github.com/TuringLang/Turing.jl/pull/1275#discussion_r434240387)を参照）。

# 例

```julia
α_0 = 2.0
θ_0 = inv(3.0)
x = [1.5, 2.0]
N = length(x)

@model function inverse_gdemo(x)
    λ ~ Gamma(α_0, θ_0)
    σ = sqrt(1 / λ)
    m ~ Normal(0, σ)
    @. x ~ $(Normal(m, σ))
end

# 条件付きは次の統計量に基づいて定式化できます：
x_bar = mean(x) # サンプル平均
s2 = var(x; mean=x_bar, corrected=false) # サンプル分散
m_n = N * x_bar / (N + 1)

function cond_m(c)
    λ_n = c.λ * (N + 1)
    σ_n = sqrt(1 / λ_n)
    return Normal(m_n, σ_n)
end

function cond_λ(c)
    α_n = α_0 + (N - 1) / 2 + 1
    β_n = s2 * N / 2 + c.m^2 / 2 + inv(θ_0)
    return Gamma(α_n, inv(β_n))
end

m = inverse_gdemo(x)

sample(m, Gibbs(GibbsConditional(:λ, cond_λ), GibbsConditional(:m, cond_m)), 10)
```
