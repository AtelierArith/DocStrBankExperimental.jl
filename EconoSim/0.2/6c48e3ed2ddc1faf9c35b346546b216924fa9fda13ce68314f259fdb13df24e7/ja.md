```
SuMSy(guaranteed_income::Real,
        dem_free::Real,
        dem_settings::DemSettings,
        interval::Integer;
        seed::Real = 0,
        seed_comment = "Seed",
        guaranteed_income_comment = "Guaranteed income",
        demurrage_comment = "Demurrage",
        dep_entry = SUMSY_DEP,
        dem_free_entry = nothing)
```

デフォルトのIDを持つSuMSy構造体を作成します。IDは:sumsy-uuidに設定され、uuidはuuid4()によって生成されます。
