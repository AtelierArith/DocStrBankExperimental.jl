```
similarnames(query::AbstractString, db::Taxonomy.DB; distance::StringDistances.StringDistance=StringDistances.Levenshtein(), threshold::Float64=0.8)
similarnames(query::AbstractString; distance::StringDistances.StringDistance=StringDistances.Levenshtein(), threshold::Float64=0.8)
```

`query`に似た名前を見つけ、taxid、name、および類似性を持つ`NamedTuple`の`Vector`を返します。類似性はデフォルトでラベンシュタイン距離によって計算されます。他の距離を`StringDistances`パッケージで定義されたものに変更することもでき、distance引数で指定します。`db`を省略すると、通常は最後に作成されたデータベースである`current_db()`が自動的に呼び出されます。
