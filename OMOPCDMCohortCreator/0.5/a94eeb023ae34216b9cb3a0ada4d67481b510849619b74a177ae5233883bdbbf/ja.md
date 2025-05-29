RaceFilterPersonIDs(race_codes, conn; tab = person)

与えられた条件概念IDのリスト `race_codes` に基づいて、Personテーブルにおいて提供された人種タイプのいずれかに一致するエントリを持つ個人をデータベースから返します。

# 引数:

  * `race_codes` - `race_concept_id` のベクター; `Integer` のサブタイプである必要があります
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Personテーブルを表す `SQLTable`; デフォルトは `person`

# 戻り値

  * `ids::Vector{Int64}` - フィルタリングの結果として得られた人物のリスト
