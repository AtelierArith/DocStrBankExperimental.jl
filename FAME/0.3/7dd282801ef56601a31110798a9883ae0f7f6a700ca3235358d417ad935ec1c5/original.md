```
listdb(db::FameDatabase, [wc; filters...])
```

List objects in the database that match the given wildcard and filters. Return a [`Vector{FameObject}`](@ref FameObject).

The wildcard `wc` is a string containing wildcard characters. '^' matches any one character, while '?' matches any zero or more characters. If not given, the  default is '?' which would list the entire database.

The filters:

  * `alias::Bool` - whether or not to match alias names.
  * `class::String` - which class of object to match. Multiple classes can be given in a comma-separated string, e.g., `class="SERIES,SCALAR"`.
  * `type::String` - which type of object to match, e.g., `type="NUMERIC,PRECISION"`.
  * `freq::String` - which frequency of object to match, e.g., `freq="QUARTERLY"`.
