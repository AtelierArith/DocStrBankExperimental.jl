```
v = sd[k]
```

Argument `sd` is a SortedDict and `k` is a key. In an expression, this retrieves the value (`v`) associated with the key (or `KeyError` if none). On the left-hand side of an assignment, this assigns or reassigns the value associated with the key. (For assigning and reassigning, see also `insert!` below.) Time: O(*c* log *n*)
