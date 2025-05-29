```
StateActionReward(m::Union{MDP,POMDP})
```

状態と行動のみに依存する報酬関数を堅牢に作成します。

`reward(m, s, a)` が実装されている場合、それが使用されます。そうでない場合、MDPの場合は `reward(m, s, a, sp)` の平均、POMDPの場合は `reward(m, s, a, sp, o)` の平均が使用されます。

# 例

```jldoctest
using POMDPs
using POMDPModels
using POMDPTools

m = BabyPOMDP()

rm = StateActionReward(m)

rm(true, true)

# 出力

-15.0
```
