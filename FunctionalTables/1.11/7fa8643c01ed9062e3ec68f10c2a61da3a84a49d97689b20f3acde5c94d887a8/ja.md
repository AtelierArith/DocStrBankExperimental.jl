```julia
aggregator(f)

```

関数をラップして、`FunctionalTable` の列をインデックスを無視して単一の行を持つテーブルに列ごとにマッピングします。クロージャを返します。

# 例

```julia
map(aggregator(mean), by(ft, :col))
```

は `:col` でグループ化した後に平均を計算します。
