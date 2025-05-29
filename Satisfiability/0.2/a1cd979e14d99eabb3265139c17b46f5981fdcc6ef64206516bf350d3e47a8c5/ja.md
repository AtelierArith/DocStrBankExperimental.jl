```
@satvariable(a, Int)
b = int2bv(a, 8)
```

指定された長さのBitVectorへの変換を表すIntExpr aをラップします。この操作は高いオーバーヘッドがあり、ソルバーのパフォーマンスに影響を与える可能性があります。
