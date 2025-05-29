```
get_datetime_for_doy_hour(doy, hour=12; year = 2030)
```

指定された年の日*の*年と時間のためのDateTimeを作成します。時間は正午がデフォルトで、年は2030年に設定されています。この年は、関数が呼び出される年と地球の軸の歳差があまり変わらない近い未来です。小数時間も指定できます。

# 例

```jldoctest output = false
get_datetime_for_doy_hour(2; year = 2021)
# output
2021-01-02T12:00:00
```
