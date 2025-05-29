```
split(namedtuple, symbol(s)|Tuple)
```

Generate two namedtuples, the first with only the fields in the second arg, the second with all but the fields in the second arg, such that `merge(split(nt, ks)...) == nt` when `ks` contains the first fields of `nt`.
