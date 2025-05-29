GenderFilterPersonIDs(gender*codes; tab = visit*occurrence)

指定された訪問概念IDのリストに基づいて、`gender_codes`を使用して、少なくとも1つのエントリがPersonテーブルにあり、提供された性別タイプのいずれかに一致する個人をデータベースから返すSQLステートメントを生成します。

# 引数:

  * `visit_codes` - `gender_concept_id`のベクター; `Integer`のサブタイプでなければなりません

# キーワード引数:

  * `tab` - Personテーブルを表す`SQLTable`; デフォルトは`person`

# 戻り値

  * `sql::String` - このフィルターを実行するSQL表現
