```
get_elnom_load(data, load_idx, year_idx, hour_idxs) -> ed::Float64 (MWh)

get_elnom_load(data, load_idxs, year_idx, hour_idxs) -> ed::Float64 (MWh) (sum)

get_elnom_load(data, pair(s), year_idx, hour_idxs) -> ed::Float64 (MWh) (sum)
```

`load_idx`または`load_idxs`に対応する負荷要素によるエネルギー負荷を返します。`year_idx`と`hour_idx`について注意してください。`year_idx`はインデックスまたは年の文字列（例："y2030"）である可能性があります。

ペア(s)が指定されている場合、ペアによって負荷要素をフィルタリングします。すなわち、pairs = ("nation"=>"narnia", "read_type"=>"residential")。
