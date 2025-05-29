```
GoalDependentPolicyHeuristic(policies::Dict, [default])
```

計画の[`Specification`](@ref)sを[`PolicySolution`](@ref)sにマッピングする辞書をラップします。特定の仕様が与えられると、ヒューリスティックは対応するポリシーを検索し、その状態の価値の否定された推定値をヒューリスティックの目標距離推定値として返します。

`default`が提供されている場合、これは辞書に見つからない仕様`spec`の新しいポリシー`policy = default(domain, state, spec)`を構築するために使用されます。そうでない場合は、エラーがスローされます。
