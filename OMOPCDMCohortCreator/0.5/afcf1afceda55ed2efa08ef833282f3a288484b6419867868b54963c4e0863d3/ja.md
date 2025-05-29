GenderFilterPersonIDs(gender*codes, conn; tab = visit*occurrence)

与えられた訪問コンセプトIDのリスト `gender_codes` に基づいて、データベースから少なくとも1つのエントリがPersonテーブルに存在し、提供された性別タイプのいずれかに一致する個人を返します。

# 引数:

  * `visit_codes` - `gender_concept_id` のベクター; `Integer` のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Personテーブルを表す `SQLTable`; デフォルトは `person`

# 戻り値

  * `ids::Vector{Int64}` - フィルタリングの結果得られた個人のリスト
