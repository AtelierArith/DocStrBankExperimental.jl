```
CompressedBeliefPolicy
```

圧縮された信念状態MDPのベースポリシーを真のPOMDPのポリシーにマッピングします。

## フィールド

  * `m::CompressedBeliefMDP`: 圧縮された信念状態MDP。
  * `base_policy::Policy`: 圧縮された信念状態MDPでの意思決定に使用されるベースポリシー。

## コンストラクタ

```
CompressedBeliefPolicy(m::CompressedBeliefMDP, base_policy::Policy)
```

指定された圧縮された信念状態MDPとベースポリシーを使用して`CompressedBeliefPolicy`を構築します。

## 使用例

```julia
policy = solve(solver, pomdp)
s = initialstate(pomdp)
a = action(policy, s) # 状態sに対するおおよその最適アクションを返します
v = value(policy, s)  # 状態sに対するおおよその最適値を返します
```
