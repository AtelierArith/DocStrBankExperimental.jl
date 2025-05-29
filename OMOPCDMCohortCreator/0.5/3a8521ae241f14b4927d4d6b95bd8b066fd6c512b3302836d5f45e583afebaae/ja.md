StateFilterPersonIDs(states; tab = location, join_tab = person)

与えられた州のリスト `states` に基づいて、データベースから提供された州リストに見つかった個人を返すSQL文を生成します。

# 引数:

  * `states` - 州の略称のベクター; `AbstractString` のサブタイプである必要があります

# キーワード引数:

  * `tab` - Locationテーブルを表す `SQLTable`; デフォルトは `location`
  * `join_tab` - Personテーブルを表す `SQLTable`; デフォルトは `person`

# 戻り値

  * `sql::String` - このフィルタを実行するSQL表現
