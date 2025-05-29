```
RXday(C::ClimGrid; days=5)
```

年間最大連続x日降水量（デフォルトはdays=5）。

RRkjを期間jのkで終了する5日間の降水量とします。すると、期間jの最大5日間の値は次のようになります：

Rx5dayj = max (RRkj)
