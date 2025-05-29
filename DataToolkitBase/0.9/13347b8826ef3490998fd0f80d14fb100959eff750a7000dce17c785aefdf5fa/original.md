```
SmallDict{K, V}
```

A little (ordered) dictionary type for a small number of keys. Rather than doing anything clever with hashes, it just keeps a list of keys, and a list of values.

For a small number of items, this has time and particularly space advantages over a standard dictionary — a Dict{String, Any}("a" => 1) is about 4x larger than the equivalent SmallDict. Further testing indicates this provides a ~40% reduction on the overall in-memory size of a `DataCollection`.
