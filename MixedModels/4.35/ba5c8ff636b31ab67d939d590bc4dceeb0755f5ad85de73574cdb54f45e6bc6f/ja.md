```
 MixedModelProfile{T<:AbstractFloat}
```

[`LinearMixedModel`](@ref) の尤度プロファイルを表す型で、関連する補間スプラインを含みます。

プロファイルを計算するために [`profile`](@ref) 関数が使用され、[`confint`](@ref) は `MixedModelProfile` から信頼区間を構築するための便利なメソッドを提供します。

!!! note
    正確なフィールドとその表現は実装の詳細と見なされ、**公開API** の一部ではありません。

