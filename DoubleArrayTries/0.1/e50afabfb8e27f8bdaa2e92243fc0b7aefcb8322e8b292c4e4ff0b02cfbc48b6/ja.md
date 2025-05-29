```
decode(dat::DoubleArrayTrie, i::Int)
```

id `i` を取得し、トライ内の対応する文字列を返します。もし `i <= 0 || i > length(dat)` の場合、常に `nothing` を返します。
