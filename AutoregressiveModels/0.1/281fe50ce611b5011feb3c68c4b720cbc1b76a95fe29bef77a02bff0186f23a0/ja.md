```
coef(r::VectorAutoregression, yid, xid, lag::Integer=1)
```

`r`の変数`yid`に対する変数`xid`の係数推定値を、遅れ`lag`で返します。`yid`と`xid`は`Symbol`型の変数名または整数インデックスであることができます。`var.nocons`が`true`でない限り、切片項は常に`:constant`と名付けられ、インデックスは`1`です。
