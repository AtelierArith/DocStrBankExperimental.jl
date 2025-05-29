GetDatabaseCohorts(conn; tab=cohort)

与えられた `DataFrame` は、データベースに関連付けられたすべてのユニークなコホート*定義*IDを返します。

# 引数:

  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - コホートテーブルを表す `SQLTable` ; デフォルトは `cohort`

# 戻り値

  * `df::DataFrame` - 列 `:cohort_definition_id` から構成される1列の `DataFrame`
