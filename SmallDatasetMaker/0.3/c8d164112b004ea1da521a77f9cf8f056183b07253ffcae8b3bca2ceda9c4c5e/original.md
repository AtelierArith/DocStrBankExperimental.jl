Given a series of `DataFrame`s, `difftables(df0::AbstractDataFrame, dfs::AbstractDataFrame...; ignoring = Cols())` returns `report::DataFrame` with columns

  * `:nrow`: number of rows of each `DataFrame`.
  * `:ncol`: number of columns of each `DataFrame`.
  * `:cols_lack`: lack of columns comparing to `df0`.
  * `:cols_add`:  extra columns comparing to `df0`.

This function is useful for update an existing dataset (where the new data might have unidentical column names).
