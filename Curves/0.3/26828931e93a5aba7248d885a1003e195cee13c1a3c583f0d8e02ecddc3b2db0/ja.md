```
get_tenor(x:: Integer):: Tenor
```

与えられた日数をテナーに変換します。

次のマッピングが使用されます（`get_days`の正確な逆）：TDays => 1, TWeeks => 7, TMonths => 30, TYears => 365
