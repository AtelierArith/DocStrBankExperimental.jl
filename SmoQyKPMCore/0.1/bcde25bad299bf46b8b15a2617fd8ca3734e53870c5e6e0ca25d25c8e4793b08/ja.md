```
kpm_lmul!(
    A, kpm_expansion::KPMExpansion, v::T,
    tmp = zeros(eltype(v), size(v)..., 3)
) where {T<:AbstractVecOrMat}
```

$$
v = F(A) \cdot v
$$

を評価し、$v$ をインプレースで修正します。ここで、$F(A)$ はチェビシェフ展開によって表されます。`A` は、`A(u,v)` として呼び出すことができる関数であり、$u = A\cdot v$ を評価し、$u$ をインプレースで修正するか、または操作 `mul!(u, A, v)` が定義されている型です。最後に、配列 `tmp` は動的メモリ割り当てを避けるために使用されます。
