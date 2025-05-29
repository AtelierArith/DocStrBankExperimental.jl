insertcolsbefore(t, before, map::Pair...)

各ペア `name => col` が `map` において、列 `col` を名前 `name` で `before` の前に挿入します。新しいテーブルを返します。

# 例

```
t = table([0.01, 0.05], [2,1], [3,4], names=[:t, :x, :y], pkey=:t)
insertcolsbefore(t, :x, :w => [0,1])
```
