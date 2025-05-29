GraphProperties(diff::Diff)

与えられた [`Diff`](@ref) からグラフのプロパティの差分を作成します。 [`Diff`](@ref) を適用した後のグラフのプロパティは `get_properties(graph) + GraphProperties(diff)` になります。diffを元に戻す場合は、`get_properties(graph) - GraphProperties(diff)` です。
