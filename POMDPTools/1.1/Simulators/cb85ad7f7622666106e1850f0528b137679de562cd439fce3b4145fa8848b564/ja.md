```
stepthrough(problem, policy, [spec])
stepthrough(problem, policy, [spec], [rng=rng], [max_steps=max_steps])
stepthrough(mdp::MDP, policy::Policy, [init_state], [spec]; [kwargs...])
stepthrough(pomdp::POMDP, policy::Policy, [up::Updater, [initial_belief, [initial_state]]], [spec]; [kwargs...])
```

シミュレーションイテレータを作成します。これは、シミュレーションが実行される際に各ステップの結果を出力するために、forループ構文で使用されることを意図しています。

例:

```
pomdp = BabyPOMDP()
policy = RandomPolicy(pomdp)

for (s, a, o, r) in stepthrough(pomdp, policy, "s,a,o,r", max_steps=10)
    println("状態 $s にいます")
    println("アクション $a を取りました")
    println("観測 $o と報酬 $r を受け取りました")
end
```

オプションの `spec` 引数は、文字列、シンボルのタプル、または単一のシンボルであり、`SimHistory` オブジェクトで呼び出される [`eachstep`](@ref) と同じパターンに従います。

内部では、この関数は `spec` を持つ `StepSimulator` を作成し、`spec` を除くすべての引数を使用して `simulate` を呼び出すことによって `[PO]MDPSimIterator` を返します。すべてのキーワード引数は `StepSimulator` コンストラクタに渡されます。
