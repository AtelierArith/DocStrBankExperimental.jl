GetPatientVisits(ids; tab = visit_occurrence)

指定された患者リストのすべての `visit_occurrence_id` を返す SQL ステートメントを返します。

# 引数:

  * `ids` - `person_id` のリスト; 各 ID は `Integer` のサブタイプでなければなりません。

# キーワード引数:

  * `tab` - Visit Occurrence テーブルを表す `SQLTable`; デフォルトは `visit_occurrence`

# 戻り値

  * `df::DataFrame` - `:person_id` と `:visit_occurrence_id` の列からなる二列の `DataFrame`
