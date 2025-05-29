GetDrugConcepts(drug*exposure*ids; tab = drug_exposure)

与えられた `drug_exposure_id` のリストに対して `drug_concept_id` を取得する SQL 文を返します。

# 引数:

  * `drug_exposure_ids` - `drug_exposure_id` のリスト; 各 ID は `Integer` のサブタイプでなければなりません

# キーワード引数:

  * `tab` - `drug*exposure` テーブルを表す `SQLTable`; デフォルトは `drug*exposure`

# 戻り値

  * `df::DataFrame` - `:drug_exposure_id` と `:drug_concept_id` の列からなる二列の `DataFrame`
