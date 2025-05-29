```
rename(t, map::Pair...)
```

各ペア `col => newname` に対して、`map` の中で `newname` を `t` の列 `col` の新しい名前として設定します。新しいテーブルを返します。

# 例

```
t = table([0.01, 0.05], [2,1], names=[:t, :x])
rename(t, :t => :time)
```
