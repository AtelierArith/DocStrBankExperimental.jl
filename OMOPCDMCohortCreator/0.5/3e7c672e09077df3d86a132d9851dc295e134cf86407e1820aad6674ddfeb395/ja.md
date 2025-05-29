GetDatabasePersonIDs(conn; tab = person)

データベースからすべてのユニークな `person_id` を取得します。

# 引数:

  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Personテーブルを表す `SQLTable`；デフォルトは `person`

# 戻り値

  * `ids::Vector{Int64}` - 人のリスト
