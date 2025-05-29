```
kpm_moments!(
    μ::AbstractVector, A, kpm_expansion::KPMExpansion, U::T, V::T,
    tmp = zeros(eltype(V), size(V)..., 3)
) where {T<:AbstractVecOrMat}
```

もし $U$ と $V$ がベクトルであれば、最初の $M$ モーメントを計算して返します。

$$
\mu_m = \langle U | T_m(A^\prime) | V \rangle,
$$

ここで $A^\prime$ は `kpm_expansion.bounds` を使用して $A$ の再スケーリングされたバージョンです。もし $U$ と $V$ が行列であれば、モーメントを次のように計算します。

$$
\mu_m = \frac{1}{N} \sum_{n=1}^N \langle U_n | T_m(A^\prime) | V_n \rangle,
$$

ここで $| U_n \rangle$ と $| V_n \rangle$ はそれぞれの行列の $n$ 番目の列です。
