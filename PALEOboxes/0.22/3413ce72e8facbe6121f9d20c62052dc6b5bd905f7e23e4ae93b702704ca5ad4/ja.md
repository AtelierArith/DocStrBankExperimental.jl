```
AbstractData
```

[`AbstractSpace`](@ref)と組み合わせてフィールドを形成できるデータ型を定義します。

具体的なサブタイプは以下を実装する必要があります：

[`allocate_values`](@ref)、[`check_values`](@ref)、[`zero_values!`](@ref)、[`dof_values`](@ref)

サブタイプが数値ソルバーに対して値を提供する必要がある場合（例えば、状態変数として）、以下も実装する必要があります：

[`init_values!`](@ref)、[`copyfieldto!`](@ref)、[`copytofield!`](@ref)、[`add_field!`](@ref)、[`add_field_vec!`](@ref)

サブタイプがコンポーネントとしての表現を持つ場合、以下を実装する必要があります：[`num_components`](@ref)、[`get_components`](@ref)

サブタイプがスレッドセーフな原子的加算操作を提供する必要がある場合（例えば、タイルモデルを使用したドメイン合計のスカラー加算変数を提供するため）、フィールド値に対して[`atomic_add!`](@ref)を実装する必要があります。
