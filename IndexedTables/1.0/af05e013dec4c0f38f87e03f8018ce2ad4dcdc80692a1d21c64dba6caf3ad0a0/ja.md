```
insertcolsafter(t, after, map::Pair...)
```

各ペア `name => col` に対して `map` の中で、`after` の後に `name` という名前の列 `col` を挿入します。新しいテーブルを返します。

# 例

```
t = table([0.01, 0.05], [2,1], [3,4], names=[:t, :x, :y], pkey=:t)
insertcolsafter(t, :t, :w => [0,1])
```
