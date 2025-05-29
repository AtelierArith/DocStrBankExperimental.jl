```
polyintersect(pgon1::AbstractVector{Point}, pgon2::AbstractVector{Point})
```

2つの多角形 `pgon1` と `pgon2` の交差を定義する多角形を含む配列（空である可能性があります）を返します。

`pgon1` と `pgon2` の多角形には穴があってはならず、自己交差してはいけません。
