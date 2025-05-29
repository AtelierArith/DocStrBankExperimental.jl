```
search(measure::AbstractSimilarityMeasure, db_collection::AbstractSimStringDB, query::AbstractString;
    α=0.7, ranked=true)
```

SimStringアルゴリズムと類似度測定を使用して、文字列コレクション内の文字列を検索します。

# 引数:

  * `measure`::AbstractSimilarityMeasure - 使用する類似度測定。
  * `db_collection`::AbstractSimStringDB - 検索するデータベースコレクション。
  * `query`::AbstractString - 検索するクエリ文字列。
  * `α`::float - SimStringアルゴリズムのαパラメータ。
  * `ranked`::Boolean - 結果をランク順で返すかどうか。

# 例

```julia
db = DictDB(CharacterNGrams(2, " "));
append!(db, ["foo", "bar", "fooo"]);

search(Dice(), db, "foo"; α=0.8, ranked=true)
# 2-element Vector{Tuple{String, Float64}}:
#  ("foo", 1.0)
#  ("fooo", 0.8888888888888888)
```

# 戻り値

  * 各要素が(`string`, `similarity measure score`)の形式のタプルである結果のベクター。
