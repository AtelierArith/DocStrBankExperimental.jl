function GetDrugExposureStartDate(drug*exposure*ids; tab = drug_exposure)

```
与えられた薬剤曝露IDのリストから、それに対応する薬剤曝露開始日IDを見つけます。

# 引数:

- `drug_exposure_ids` - `drug_exposure_id`のリスト; 各IDは`Float64`のサブタイプでなければなりません


# キーワード引数:

- `tab` - 薬剤曝露テーブルを表す`SQLTable`; デフォルトは`drug_exposure`

# 戻り値

- `:drug_exposure_id`と`:drug_exposure_start_date`から構成されるSQL文
```
