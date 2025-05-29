```
parse_year_idxs(s::AbstractString) -> comparisons
```

Parse a year comparison.  Could take the following forms:

  * `"y2020"` - year 2020 only
  * `""` - All years, returns (:)
  * `"1"` - year index 1
  * `"[1,2,3]"`
