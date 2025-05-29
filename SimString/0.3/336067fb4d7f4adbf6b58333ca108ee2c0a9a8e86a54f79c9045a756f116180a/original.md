```
describe_collection(db::DictDB)
```

Basic summary stats for the DB

# Arguments

  * `db`: DictDB object

# Example

```julia
db = DictDB(CharacterNGrams(2, " "));
append!(db, ["foo", "bar", "fooo"]);
describe_collection(db)
(total_collection = 3, avg_size_ngrams = 4.5, total_ngrams = 13)

# Returns
* NamedTuples: Summary stats for the DB
```
