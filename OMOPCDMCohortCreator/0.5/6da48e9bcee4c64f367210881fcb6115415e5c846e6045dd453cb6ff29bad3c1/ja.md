GetDrugAmounts(drug*concept*ids, conn; tab = drug_strength)

与えられた薬剤の概念IDのリストから、その量を見つけます。

# 引数:

  * `drug_concept_ids` - `drug_concept_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - 薬剤*強度テーブルを表す`SQLTable`; デフォルトは`drug*strength`

# 戻り値

  * `df::DataFrame` - `:drug_concept_id`と`:amount_value`の列からなる2列の`DataFrame`
