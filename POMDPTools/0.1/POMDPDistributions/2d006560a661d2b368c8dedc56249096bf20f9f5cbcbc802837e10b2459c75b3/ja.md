```
ImplicitDistribution(sample_function, args...)
```

明示的な `pdf` を持たず、`rand` を使用してのみサンプリングできる分布を定義します。

`rand(rng, d::ImplicitDistribution)` が呼び出されるたびに、

```julia
sample_function(args..., rng)
```

が呼び出されて新しいサンプルが生成されます。

`ImplicitDistribution` は、無名関数や `do` 構文と共に使用するために設計されています。以下はその例です。

# 例

```julia
ImplicitDistribution(rng->rand(rng)^2)
```

```julia
struct MyMDP <: MDP{Float64, Int} end

function POMDPs.transition(m::MyMDP, s, a)
    ImplicitDistribution(s, a) do s, a, rng
        return s + a + 0.001*randn(rng)
    end
end

td = transition(MyMDP(), 1.0, 1)
rand(td) # 2 に近い数値を返します
```
