GetDrugConcepts(drug*exposure*ids; tab = drug_exposure)

与えられた薬剤曝露IDのリストから、それらの薬剤*概念*IDを見つけます。

# 引数:

  * `drug_exposure_ids` - `drug_exposure_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - 薬剤*曝露テーブルを表す`SQLTable`; デフォルトは`drug*exposure`

# 戻り値

  * `df::DataFrame` - `:drug_exposure_id`と`:drug_concept_id`の列からなる2列の`DataFrame`
