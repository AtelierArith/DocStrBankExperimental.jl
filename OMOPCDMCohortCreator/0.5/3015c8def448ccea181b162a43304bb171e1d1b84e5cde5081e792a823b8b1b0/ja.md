ExecuteAudit(data::DataFrame; hitech = true)

データフレームに対して監査を実行する関数で、監査およびプライバシー保護のベストプラクティスに準拠していることを確認するために `count` 列を含む必要があります。

# 引数:

  * `data::DataFrame` - 監査するデータで、`DataFrame` であり、`count` という名前の列を含む必要があります。

# キーワード引数:

  * `hitech::Bool` - プライバシー保護手法のためのHITECH基準を強制するブール値。
  * `target_column::Symbol` - 監査の対象となる列の名前（デフォルトは :count に設定）。

# 戻り値

  * `df` - 与えられた基準に従って適切に監査された `DataFrame`。
