与えられた一連の `DataFrame` に対して、`difftables(df0::AbstractDataFrame, dfs::AbstractDataFrame...; ignoring = Cols())` は `report::DataFrame` を返します。この `DataFrame` には以下の列があります。

  * `:nrow`: 各 `DataFrame` の行数。
  * `:ncol`: 各 `DataFrame` の列数。
  * `:cols_lack`: `df0` と比較して不足している列。
  * `:cols_add`: `df0` と比較して追加されている列。

この関数は、既存のデータセットを更新する際に便利です（新しいデータが異なる列名を持っている可能性があるため）。
