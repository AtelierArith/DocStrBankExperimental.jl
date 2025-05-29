```
remake(prob::SCCNonlinearProblem; u0 = missing, p = missing, probs = missing,
    parameters_alias = prob.parameters_alias, sys = missing, explicitfuns! = missing)
```

与えられた `SCCNonlinearProblem` を再構築します。`u0` は問題全体の状態ベクトルであり、適切に分割され、個々のサブプロブレムを `remake` するために使用されます。`p` は `prob` のパラメータオブジェクトです。`parameters_alias` が指定されている場合、同じパラメータオブジェクトが個々のサブプロブレムを `remake` するために使用されます。そうでない場合、`p !== missing` であれば、この関数はエラーを返し、`probs` の指定を要求します。`probs` はサブプロブレムのコレクションです。`probs` が明示的に指定されていても、`remake` に提供された `u0` の値が `probs` の値を上書きするために使用されます。`sys` は全体システムのインデックスプロバイダーです。
