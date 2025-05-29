```
kpm_moments(
    A, kpm_expansion::KPMExpansion,, R::T,
    tmp = zeros(eltype(R), size(R)..., 3)
) where {T<:AbstractVecOrMat}
```

もし $R$ がベクトルであれば、最初の $kpm_expansion.M$ モーメントを次のように計算して返します。

$$
\mu_m = \langle R | T_m(A^\prime) | R \rangle
$$

ここで $A^\prime$ は `kpm_expansion.bounds` を使用して $A$ の再スケーリングされたバージョンです。もし $R$ が行列であれば、モーメントを次のように計算します。

$$
\mu_m = \frac{1}{N} \sum_{n=1}^N \langle R_n | T_m(A^\prime) | R_n \rangle,
$$

ここで $| R_n \rangle$ は $R$ の $n$ 番目の列です。
