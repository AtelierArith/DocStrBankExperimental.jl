```
parse_hour_idxs(s::AbstractString) -> comparisons
```

Parse a year comparison.  Could take the following forms:

  * `"1"` - hour 1 only
  * `""` - All hours, returns (:)
  * `"season=>winter"` - returns "season"=>"winter"
