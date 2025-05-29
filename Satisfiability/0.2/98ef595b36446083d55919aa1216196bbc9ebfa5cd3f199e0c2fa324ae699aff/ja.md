```
@satvariable(b, BitVector, 8)
a = bv2int(b)
```

BitVectorをIntExprに変換することを表すラップされたBitVectorExpr b。整数式の値は、ラップされたBitVectorのサイズによって制限されます。この操作は高いオーバーヘッドがあり、ソルバーのパフォーマンスに影響を与える可能性があります。
