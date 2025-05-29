```
PolicyWrapper
```

計画に関する統計を収集するために設計されたポリシーの柔軟なユーティリティラッパーです。

関数、ポリシー、およびオプションでペイロード（任意の型を持つことができます）を持ちます。

関数は通常、do構文で定義されるべきです。ラッパーで`action`が呼び出されるたびに、この関数が呼び出されます。

ペイロードがない場合、ポリシーと状態/信念の2つの引数で呼び出されます。ペイロードがある場合、ポリシー、ペイロード、および現在の状態または信念の3つの引数で呼び出されます。関数は適切なアクションを返す必要があります。この関数内で`action(policy, s)`が呼び出され、ポリシー/プランナーからの統計が収集されてペイロードに保存され、例外が処理され、アクションが返されるというのがアイデアです。

コンストラクタ

`PolicyWrapper(policy::Policy; payload=nothing)`

# 例

```julia
using POMDPModels
using POMDPToolbox

mdp = GridWorld()
policy = RandomPolicy(mdp)
counts = Dict(a=>0 for a in actions(mdp))

# ペイロードあり
statswrapper = PolicyWrapper(policy, payload=counts) do policy, counts, s
    a = action(policy, s)
    counts[a] += 1
    return a
end

h = simulate(HistoryRecorder(max_steps=100), mdp, statswrapper)
for (a, count) in payload(statswrapper)
    println("policy chose action $a $count of $(n_steps(h)) times.")
end

# ペイロードなし
errwrapper = PolicyWrapper(policy) do policy, s
    try
        a = action(policy, s)
    catch ex
        @warn("Caught error in policy; using default")
        a = :left
    end
    return a
end

h = simulate(HistoryRecorder(max_steps=100), mdp, errwrapper)
```

# フィールド

  * `f::F`
  * `policy::P`
  * `payload::PL`
