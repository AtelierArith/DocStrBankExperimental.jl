```
intensities_decode(x, its)
```

データセット `x` の強度値を元の値の範囲に逆変換し、新しいデータセットまたはベクトルを返します。`its` 引数には、`intensities_encode` によって返される変換に関する情報が含まれています。

元の変換が 0.0 または 1.0（最小値と最大値）以外の分位数を使用している場合、範囲は切り捨てられることに注意してください。

# 例:

```
x = randn(5, 4)
xint, its = intensities_encode(x, 0.05)
dbm = fitdbm(xint)
xgen = samples(dbm, 5)
intensities_decode(xgen, its)
```
