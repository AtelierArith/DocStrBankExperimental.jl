ConditionFilterPersonIDs(condition*codes; tab = condition*occurrence)

条件概念IDのリスト `condition_codes` を与えると、Condition Occurrence テーブルにおいて、提供された条件タイプのいずれかに一致するエントリを少なくとも1つ持つ個人をデータベースから返す SQL ステートメントを生成します。

# 引数:

  * `condition_codes` - `condition_concept_id` のベクター; `Integer` のサブタイプでなければなりません

# キーワード引数:

  * `tab` - Condition Occurrence テーブルを表す `SQLTable`; デフォルトは `condition_occurrence`

# 戻り値

  * `sql::String` - このフィルタを実行する SQL 表現
