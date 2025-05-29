```
ActionGoal(action::Term, [constraints, step_cost])
```

[`Goal`](@ref) 仕様は、`action` が最終ステップとして実行されることを要求します。オプションで、オブジェクト `constraints` を指定できます。これらは、アクションの変数パラメータに対する静的制約であるか、最終状態で満たされなければならない述語です。解の各ステップのコストは `step_cost` で、デフォルトは 1.0 です。
