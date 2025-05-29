VisitFilterPersonIDs(visit*codes, conn; tab = visit*occurrence)

与えられた訪問概念IDのリスト `visit_codes` に基づいて、Visit Occurrence テーブルから提供された訪問コードのいずれかに一致する患者を返します。

# 引数:

  * `visit_codes` - `visit_concept_id` のベクター; `Integer` のサブタイプである必要があります
  * `conn` - DBInterface を使用したデータベース接続

# キーワード引数:

  * `tab` - Visit Occurrence テーブルを表す `SQLTable`; デフォルトは `visit_occurrence`

# 戻り値

  * `ids::Vector{Int64}` - フィルターの結果として得られた人物のリスト
