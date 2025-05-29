```
relayout_matrix!(
    daf::DafWriter,
    rows_axis::AbstractString,
    columns_axis::AbstractString,
    name::AbstractString;
    [overwrite::Bool = false]
)::Nothing
```

与えられた行列プロパティが `daf` に存在し（列優先レイアウト）、`rows_axis` と `columns_axis` に対して `name` がある場合、[`relayout!`](@ref) を呼び出して、行優先の結果を保存します（つまり、軸を反転させたものです）。

これは、[`empty_dense_matrix!`](@ref) または [`empty_sparse_matrix!`](@ref) を呼び出した後に、行列の両方のレイアウトが `def` に保存されることを保証するのに役立ちます。[`set_matrix!`](@ref) を呼び出す際には、単に（デフォルトの）`relayout = true` を指定するだけで簡単です。

最初に、`rows_axis` と `columns_axis` が `daf` に存在し、これらに対して `name`（列優先）の行列プロパティが存在することを確認します。`overwrite`（デフォルト）の場合は、*反転された* `rows_axis` と `columns_axis` に対して `name` 行列が存在しないことも確認します。

!!! note
    `Daf` がデータを保存する方法の制限は、正方形のデータが一つの（列優先）レイアウトにのみ保存されることです（例：セル間の重み付き有向グラフを保存するために、各セルの列がそのセルから他のセルへの出力重みを保持する出力*重み行列を保存することができます。この場合、各セルの行が他のセルからの入力重みになるように行列を行優先順に再配置するように `Daf` に要求することは**できません**。代わりに、各セルの列が入力重みを保持する別の入力*重み行列を明示的に保存する必要があります）。

