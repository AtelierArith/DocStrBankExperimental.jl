```
positions(model::ABM{<:DiscreteSpace}) → ns
```

離散空間を持つモデルのすべての位置に対するイテレータを返します。

```
positions(model::ABM{<:DiscreteSpace}, by::Symbol) → ns
```

離散空間を持つモデルのすべての位置を返し、引数 `by` を使用してソートします。`by` は次のいずれかです：

  * `:random` - ランダムにソートされます
  * `:population` - 位置は、どれだけ多くのエージェントを収容できるかに応じてソートされます。より多くの人口を持つ位置が最初に来ます。
