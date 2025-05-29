RaceFilterPersonIDs(race_codes; tab = person)

指定された `race_concept_id` のリストに基づいて、Person テーブルに少なくとも 1 つのエントリがあり、提供されたレースタイプのいずれかに一致する個人をデータベースから返す SQL ステートメントを生成します。

# 引数:

  * `race_codes` - `race_concept_id` のベクター; `Integer` のサブタイプである必要があります

# キーワード引数:

  * `tab` - Person テーブルを表す `SQLTable`; デフォルトは `person`

# 戻り値

  * `sql::String` - このフィルターを実行する SQL 表現
