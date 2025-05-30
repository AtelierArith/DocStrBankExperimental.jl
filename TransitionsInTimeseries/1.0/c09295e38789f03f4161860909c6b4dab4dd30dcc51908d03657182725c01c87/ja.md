```
estimate_changes(config::ChangesConfig, x [,t]) → result
```

入力時系列 `x` の可能な遷移を、設定タイプ `config` で指定されたアプローチを使用して推定します。`t` は `x` に対応する時間ベクトルで、デフォルトでは `eachindex(x)` になります。

出力は [`ChangesResults`](@ref) のサブタイプとして返されます。出力の特定の形式は `config` に依存し、そのドキュメントに記載されています。型に関係なく、`result` は常に [`significant_transitions`](@ref) に渡して、さまざまな有意性検定を使用して統計的に有意な可能性のある遷移を推測することができます。
