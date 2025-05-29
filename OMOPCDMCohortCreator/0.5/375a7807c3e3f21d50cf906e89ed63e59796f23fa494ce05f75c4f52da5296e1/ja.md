GetVisitProcedure(visit*ids; tab = procedure*occurrence)

指定された `visit_id` のリストに基づいて、その訪問に関連する手続きを見つける SQL ステートメントを生成します。

# 引数:

  * `visit_ids` - `visit_id` のリスト; 各 ID は `Integer` のサブタイプでなければなりません

# キーワード引数:

  * `tab` - Procedure Occurrence テーブルを表す `SQLTable`; デフォルトは `procedure_occurrence`

# 戻り値

  * `df::DataFrame` - `:visit_occurrence_id` と `:procedure_concept_id` の列からなる二列の `DataFrame`
