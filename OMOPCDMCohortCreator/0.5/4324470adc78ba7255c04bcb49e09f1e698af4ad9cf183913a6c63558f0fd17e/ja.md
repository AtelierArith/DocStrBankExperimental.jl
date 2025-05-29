GetDrugAmounts(drug*concept*ids; tab = drug_strength)

与えられた `drug_concept_id` のリストに対して `amount_value` を取得する SQL ステートメントを返します。

# 引数:

  * `drug_concept_ids` - `drug_concept_id` のリスト; 各 ID は `Integer` のサブタイプでなければなりません。

# キーワード引数:

  * `tab` - `drug*strength` テーブルを表す `SQLTable`; デフォルトは `drug*strength`

# 戻り値

  * `df::DataFrame` - `:drug_concept_id` と `:amount_value` の列からなる二列の `DataFrame`
