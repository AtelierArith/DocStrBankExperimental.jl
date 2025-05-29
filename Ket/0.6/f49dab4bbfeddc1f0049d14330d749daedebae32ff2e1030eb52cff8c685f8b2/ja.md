```
permute_systems(X::AbstractVector, perm::AbstractVector, dims::AbstractVector = _equal_sizes(X))
```

ベクトル `X` のサブシステムの順序を、順列 `perm` に従ってサブシステムの次元 `dims` で入れ替えます。引数 `dims` が省略された場合、2つの同じサイズのサブシステムが仮定されます。
