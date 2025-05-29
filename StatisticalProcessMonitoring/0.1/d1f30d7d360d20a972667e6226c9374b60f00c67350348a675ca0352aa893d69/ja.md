```
categorical_to_index(g::AbstractVector, table::AbstractMatrix)
```

カテゴリ変数 `g` をテーブル内の対応するインデックスに変換します。

# 引数

  * `g::AbstractVector`: 変換するカテゴリ変数。
  * `table::AbstractMatrix`: すべての可能なカテゴリを含むテーブル。

# 戻り値

  * `Int`: テーブル内のカテゴリのインデックス。

# 発生する例外

  * インデックスが見つからない場合は `ErrorException` が発生します。

# 例

```
x = randn(500, 3)
df, table, qtls = create_table(x, [2 for _ in eachcol(x)])
xnew = randn(3)
g = categorize_data(xnew, qtls)
idx = categorical_to_index(g, table)
```
