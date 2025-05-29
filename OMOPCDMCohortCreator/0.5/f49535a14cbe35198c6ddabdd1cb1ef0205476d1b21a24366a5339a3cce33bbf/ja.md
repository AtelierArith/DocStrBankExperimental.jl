GetDrugExposureIDs(ids, conn; tab = drug_exposure)

与えられた人物IDのリストから、その薬物曝露を見つけます。

# 引数:

  * `ids` - `person_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - 薬物曝露テーブルを表す`SQLTable`; デフォルトは`drug*exposure`

# 戻り値

  * `df::DataFrame` - `:person_id`と`:drug_exposure_id`の列からなる2列の`DataFrame`
