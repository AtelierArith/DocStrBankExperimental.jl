```
search(measure::AbstractSimilarityMeasure, db_collection::AbstractSimStringDB, query::AbstractString;
    α=0.7, ranked=true)
```

Search for strings in a string collection using the SimString algorithm and a similarity measure.

# Arguments:

  * `measure`::AbstractSimilarityMeasure - The similarity measure to use.
  * `db_collection`::AbstractSimStringDB - The database collection to search.
  * `query`::AbstractString - The query string to search for.
  * `α`::float - The α parameter for the SimString algorithm.
  * `ranked`::Boolean - Whether to return the results in ranked order.

# Example

```julia
db = DictDB(CharacterNGrams(2, " "));
append!(db, ["foo", "bar", "fooo"]);

search(Dice(), db, "foo"; α=0.8, ranked=true)
# 2-element Vector{Tuple{String, Float64}}:
#  ("foo", 1.0)
#  ("fooo", 0.8888888888888888)
```

# Returns

  * A Vector of results, where each element is a Tuple of the form (`string`, `similarity measure score`).
