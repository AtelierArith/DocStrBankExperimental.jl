```
is_rimhook(R::BitVector, idx::Integer, len::Integer)
```

`R[idx:idx+len]` は、`R` に対応する分割のヤング図においてリムフックを形成する、もし `R[idx] == true` かつ `R[idx+len] == false` であるならば。
