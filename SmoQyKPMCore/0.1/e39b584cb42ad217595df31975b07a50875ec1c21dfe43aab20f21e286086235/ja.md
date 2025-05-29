```
kpm_mul!(
    v′::T, A, kpm_expansion::KPMExpansion, v::T,
    tmp = zeros(eltype(v), size(v)..., 3)
) where {T<:AbstractVecOrMat}
```

$$
v^\prime = F(A) \cdot v
$$

を評価し、結果を $v^\prime$ に書き込みます。ここで、$F(A)$ はチェビシェフ展開によって表されます。`A` は、`A(u,v)` として呼び出すことができる関数で、$u = A\cdot v$ を評価し、$u$ をインプレースで変更するか、または操作 `mul!(u, A, v)` が定義されている型です。最後に、配列 `tmp` は動的メモリ割り当てを避けるために使用されます。
