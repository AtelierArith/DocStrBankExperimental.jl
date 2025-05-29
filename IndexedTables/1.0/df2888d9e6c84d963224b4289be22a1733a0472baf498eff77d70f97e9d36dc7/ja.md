```
summarize(f, t, by = pkeynames(t); select = Not(by), stack = false, variable = :variable)
```

テーブルに対して列ごとに要約関数を適用します。グループ化されていない場合は`NamedTuple`を返し、グループ化されている場合はテーブルを返します。同じ要約関数の異なる列の結果をスタックするには`stack=true`を使用します。

# 例

```
using Statistics

t = table([1, 2, 3], [1, 1, 1], names = [:x, :y])

summarize((mean, std), t)
summarize((m = mean, s = std), t)
summarize(mean, t; stack=true)
summarize((mean, std), t; select = :y)
```
