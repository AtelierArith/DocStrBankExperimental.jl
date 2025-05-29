```
describe_collection(db::DictDB)
```

DBの基本的な要約統計

# 引数

  * `db`: DictDBオブジェクト

# 例

```julia
db = DictDB(CharacterNGrams(2, " "));
append!(db, ["foo", "bar", "fooo"]);
describe_collection(db)
(total_collection = 3, avg_size_ngrams = 4.5, total_ngrams = 13)

# 戻り値
* NamedTuples: DBの要約統計
```
