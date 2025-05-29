```
rekey(A, (1:10, [:a, :b]))
rekey(A, 2 => [:a, :b])
rekey(A, :y => [:a, :b])
```

Rekey a KeyedArray via `Tuple`s or `Pair`s, `dim => newkey`. If `A` also has named dimensions then you can also pass `dimname => newkey`.
