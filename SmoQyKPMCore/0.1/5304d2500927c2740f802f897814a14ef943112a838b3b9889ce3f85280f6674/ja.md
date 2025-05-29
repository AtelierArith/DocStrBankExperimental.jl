```
kpm_lmul!(
    A, coefs::AbstractVector, v::T, bounds,
    tmp = zeros(eltype(v), size(v)..., 3)
) where {T<:AbstractVecOrMat}
```

$$
F(A) \cdot v
$$

を評価し、$v$をインプレースで修正します。ここで、$F(A)$はチェビシェフ展開によって表されます。`A`は、`A(u,v)`として呼び出すことができる関数で、$u = A\cdot v$を評価し、$u$をインプレースで修正するか、または操作`mul!(u, A, v)`が定義されている型です。ベクトル`coefs`は、$F(A)$を近似するためのチェビシェフ展開係数を含んでおり、$A$の固有スペクトルは`bounds`引数で指定された区間`(bounds[1], bounds[2])`に含まれています。ベクトル`v`は、$F(A)$のチェビシェフ展開で掛け算されるベクトルです。最後に、`tmp`は動的メモリ割り当てを避けるために使用される配列です。
