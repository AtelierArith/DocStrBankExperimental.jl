StateFilterPersonIDs(states, conn; tab = location, join_tab = person)

与えられた州のリスト `states` に基づいて、データベースから指定された州リストに見つかった個人を返します。

# 引数:

  * `states` - 州の略称のベクター; `AbstractString` のサブタイプである必要があります
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Locationテーブルを表す `SQLTable`; デフォルトは `location`
  * `join_tab` - Personテーブルを表す `SQLTable`; デフォルトは `person`

# 戻り値

  * `ids::Vector{Int64}` - フィルタの結果として得られた個人のリスト
