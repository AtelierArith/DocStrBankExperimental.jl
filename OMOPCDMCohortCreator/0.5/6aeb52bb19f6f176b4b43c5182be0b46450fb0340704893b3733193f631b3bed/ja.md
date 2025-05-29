GetDatabasePersonIDs(; tab = person)

データベースからすべてのユニークな `person_id` を取得するSQL文を返します。

# キーワード引数:

  * `tab` - Personテーブルを表す `SQLTable`；デフォルトは `person`

# 戻り値

  * `sql::String` - `String` としての準備されたSQL文
