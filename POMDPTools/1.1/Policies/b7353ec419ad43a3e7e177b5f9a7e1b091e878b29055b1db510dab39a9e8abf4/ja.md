```
evaluate(m::MDP, p::Policy)
evaluate(m::MDP, p::Policy; rewardfunction=POMDPs.reward)
```

MDP上のポリシーの値をKochenderferの*Decision Making Under Uncertainty*の式4.2.2のアプローチを使用して計算します。

状態を値にマッピングするDiscreteValueFunctionを返します。

# 例

```
using POMDPTools, POMDPModels
m = SimpleGridWorld()
u = evaluate(m, FunctionPolicy(x->:left))
u([1,1]) # 状態[1,1]から常に左に移動する場合の値
```
