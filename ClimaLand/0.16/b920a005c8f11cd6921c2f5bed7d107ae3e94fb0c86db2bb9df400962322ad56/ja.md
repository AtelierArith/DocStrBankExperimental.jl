```
set_atmos_ts!(ts_in, atmos::PrescribedAtmosphere{FT}, p)
```

事前に割り当てられた ts_in `Field` を、大気から計算された熱力学的状態で満たします。
