```
create_capex_obj!(config, data) ->
```

capex*objおよびtransmission*capex*obj列を作成します。これは目的関数で見られるcapexコストです。これはByYear列であり、year*onのときのみ非ゼロです。year_on以降に未建設の発電機のためにcapexに設定され、既存の発電機のためには容量拡張が考慮されないため、すでに建設された容量には0に設定されます。
