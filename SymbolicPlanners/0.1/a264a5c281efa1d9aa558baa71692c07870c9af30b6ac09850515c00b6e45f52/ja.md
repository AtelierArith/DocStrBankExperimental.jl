```julia
abstract type Solution
```

計画問題の解決策のための抽象型。最小限、`Solution`は特定のステップ`t`または特定の`state`でどのアクションを実行すべきかを、[`get_action`](@ref)を実装することで定義する必要があります。
