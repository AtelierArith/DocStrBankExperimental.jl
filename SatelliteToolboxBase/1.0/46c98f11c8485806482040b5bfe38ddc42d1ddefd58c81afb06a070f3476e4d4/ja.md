```
date_to_jd(Y::Integer, M::Integer, D::Integer[, h::Integer, m::Integer, s::Number])
```

グレゴリオ暦を使用して表された日付（年 = `y`、月 = `M`（1-12）、日 = `D`、時 = `h`（0-24）、分 = `m`、秒 = `s`）をユリウス日に変換します。

`h`、`m`、および `s` が省略された場合、関数はそれらが0であると仮定します。

# 備考

このアルゴリズムは[1]から取得されました（2022-07-20にアクセス）。

# 参考文献

  * **[1]**: https://quasar.as.utexas.edu/BillInfo/JulianDatesG.html

```
