```
transform(t::Table, changes::Pair...)
```

`t`の列を変換します。`changes`の各ペア`col => value`に対して、列`col`は`AbstractVector` `value`で置き換えられます。`col`が既存の列でない場合は、新しい列が作成されます。

# 例:

```
t = table([1,2], [3,4], names=[:x, :y])

# 2番目の列を[5,6]に変更
transform(t, 2 => [5,6])
transform(t, :y => :y => x -> x + 2)

# [5,6]を列:zとして追加
transform(t, :z => 5:6)
transform(t, :z => :y => x -> x + 2)

# 主キーを置き換えると、再ソートされたコピーが生成されます
t = table([0.01, 0.05], [1,2], [3,4], names=[:t, :x, :y], pkey=:t)
t2 = transform(t, :t => [0.1,0.05])

# 列:zはtの一部ではないため、新しい列が追加されます
t = table([0.01, 0.05], [2,1], [3,4], names=[:t, :x, :y], pkey=:t)
transform(t, :z => [1//2, 3//4])
```
