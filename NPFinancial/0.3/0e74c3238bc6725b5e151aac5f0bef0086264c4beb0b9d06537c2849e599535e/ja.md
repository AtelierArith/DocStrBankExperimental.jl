```
fv(rate::Real, nper::Integer, pmt::Real, pv::Real, when = :end)
```

現在価値 `pv`、期間ごとに1回複利で計算される利率 `rate`、および `nper` 期間の数を考慮して将来価値を計算します。固定支払い `pmt` は `when` 引数で指定でき、各期間の開始時 (`:begin`) または期間の終了時 (`:end`) に支払われます。

# 例

```
julia> fv(0.05, 1, 0, -100)
105.0

julia> fv(0.05, 2, 0, -100)
110.25
```
