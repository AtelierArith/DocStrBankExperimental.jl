```
function promote_to_nD(M::Array{T, N}, n::Int, fill_elem::T)
```

与えられた行列 M が n 次元構造の (n - 1) 次元スライスであると仮定し、配列を `fill_elem` で n 次元に埋めます。
