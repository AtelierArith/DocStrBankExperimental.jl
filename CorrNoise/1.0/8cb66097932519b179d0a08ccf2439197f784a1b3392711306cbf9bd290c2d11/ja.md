```
initflatrng128(xstart = 123456789, ystart = 362436069, zstart = 521288629, wstart = 88675123)
```

2^128の周期を持つフラット乱数生成器を初期化します。乱数を生成するには、通常通り`Base.rand`関数を使用します。

例:

```
rng = initflatrng128()
print([rand(rng) for i in 1:4])
```
