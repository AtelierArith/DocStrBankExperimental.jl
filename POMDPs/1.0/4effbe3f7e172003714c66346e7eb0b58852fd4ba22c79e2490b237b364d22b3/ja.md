```
observation(m::POMDP, statep)
observation(m::POMDP, action, statep)
observation(m::POMDP, state, action, statep)
```

観測分布を返します。観測分布を決定するために必要な最小限の引数でメソッドを定義するだけで済みます。

確率密度または質量関数を明示的に定義するのが難しい場合は、`POMDPModelTools.ImplicitDistribution`を使用して生成モデルを定義することを検討してください。

# 例

```julia
using POMDPModelTools # for SparseCat

struct MyPOMDP <: POMDP{Int, Int, Int} end

observation(p::MyPOMDP, sp::Int) = SparseCat([sp-1, sp, sp+1], [0.1, 0.8, 0.1])
```
