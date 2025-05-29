```
RecordGroup <: RecordAction
```

一連の [`RecordAction`](@ref) を1つのアクションにグループ化します。内部の [`RecordAction`](@ref) は独立して動作しますが、結果はグループ化された形式で収集でき、各呼び出しごとにタプルとして返されます。エントリには、インデックスまたは意味的なシンボルで後からアクセスできます。

# コンストラクタ

```
RecordGroup(g::Array{<:RecordAction, 1})
```

[`RecordAction`](@ref) の配列 `g` からなるグループを構築します。

```
RecordGroup(g, symbols)
```

# 例

```
g1 = RecordGroup([RecordIteration(), RecordCost()])
```

現在のイテレーションとコストを記録するための RecordGroup です。コストには `get_record(r,2)` または `r[2]` を使用してアクセスできます。

```
g2 = RecordGroup([RecordIteration(), RecordCost()], Dict(:Cost => 2))
```

現在のイテレーションとコストを記録するための RecordGroup で、コストには `get_record(:Cost)` または `r[:Cost]` を使用してアクセスできます。

```
g3 = RecordGroup([RecordIteration(), RecordCost() => :Cost])
```

前のコンストラクタと同じ RecordGroup ですが、少し使いやすくなっています。この最後の `g3` の2番目のエントリのすべての記録にアクセスするには、`g4[2]` または `g[:Cost]` を使用できます。最初のものは `g4[1]` でのみアクセスでき、ここではシンボルが与えられていません。
