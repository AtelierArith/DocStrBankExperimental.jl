```
basis_transform(A, B)
```

基底変換行列を計算して、非直交基底 `A` に対して `B` から移行します。これは [`basis_overlap`](@ref) を介して行います：

$$
(B^HB)^{-1}B^HA
$$
