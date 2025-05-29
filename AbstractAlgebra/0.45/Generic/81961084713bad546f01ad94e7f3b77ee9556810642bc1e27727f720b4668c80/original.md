```
is_rimhook(R::BitVector, idx::Integer, len::Integer)
```

`R[idx:idx+len]` forms a rim hook in the Young Diagram of partition corresponding to `R` iff `R[idx] == true` and `R[idx+len] == false`.
