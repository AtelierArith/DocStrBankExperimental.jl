```
incdec!(ft::FenwickTree{T}, left::Integer, right::Integer, val)
```

インデックス `left` から `val` だけ [`FenwickTree`] の値を増加させ、`right` からは減少させます。
