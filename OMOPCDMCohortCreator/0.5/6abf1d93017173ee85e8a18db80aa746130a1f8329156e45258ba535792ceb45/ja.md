ConditionFilterPersonIDs(condition*codes, conn; tab = condition*occurrence)

与えられた条件概念IDのリスト `condition_codes` に基づいて、条件発生テーブルに少なくとも1つのエントリがあり、提供された条件タイプのいずれかに一致する個人をデータベースから返します。

# 引数:

  * `condition_codes` - `condition_concept_id` のベクター; `Integer` のサブタイプである必要があります
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - 条件発生テーブルを表す `SQLTable`; デフォルトは `condition_occurrence`

# 戻り値

  * `ids::Vector{Int64}` - フィルターの結果として得られる人物のリスト
