```
get_count(co::ManifoldCountObjective, s::Symbol, mode::Symbol=:None)
```

Get the number of counts for a certain symbol `s`.

Depending on the `mode` different results appear if the symbol does not exist in the dictionary

  * `:None`:  (default) silent mode, returns `-1` for non-existing entries
  * `:warn`:  issues a warning if a field does not exist
  * `:error`: issues an error if a field does not exist
