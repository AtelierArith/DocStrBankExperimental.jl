```
CircBuff(T, b; rev=false)
```

`T`型の`b`アイテムの固定長円形バッファを作成します。

  * `rev=false`: `o[1]`は最も古い。
  * `rev=true`: `o[end]`は最も古い。

# 例

```
a = CircBuff(Int, 5)
b = CircBuff(Int, 5, rev=true)

fit!(a, 1:10)
fit!(b, 1:10)

a[1] == b[end] == 1
a[end] == b[1] == 10

value(o; ordered=false)  # 値を取得する（コピーなし）順序なしで
```
