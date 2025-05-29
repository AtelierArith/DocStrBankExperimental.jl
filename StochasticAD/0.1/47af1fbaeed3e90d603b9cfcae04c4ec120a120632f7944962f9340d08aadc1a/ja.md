```
InversionMethodDerivativeCoupling(; mode::Val = Val(:positive_weight), handle_zeroprob::Val = Val(true))
```

単変量分布から摂動を生成するための逆転法結合を指定します。`mode`の有効な選択肢は`Val(:positive_weight)`、`Val(:always_right)`、および`Val(:always_left)`です。

# 例

```jldoctest
julia> using StochasticAD, Distributions, Random; Random.seed!(4321);

julia> function X(p)
           return randst(Bernoulli(1 - p); derivative_coupling = InversionMethodDerivativeCoupling(; mode = Val(:always_right)))
       end
X (generic function with 1 method)

julia> stochastic_triple(X, 0.5)
StochasticTriple of Int64:
0 + 0ε + (1 with probability -2.0ε)
```
