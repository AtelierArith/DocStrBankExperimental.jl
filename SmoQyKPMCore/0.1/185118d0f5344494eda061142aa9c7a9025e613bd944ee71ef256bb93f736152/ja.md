```
kpm_dot(
    A, coefs::AbstractVector, bounds, U::T, V::T,
    tmp = zeros(eltype(V), size(V)..., 3)
) where {T<:AbstractVecOrMat}
```

もし $U$ と $V$ が単一のベクトルであれば、内積を計算します。

$$
\begin{align*}
S & = \langle U | F(A^\prime) | V \rangle \\
  & = \sum_{m=1}^M \langle U | c_m T_m(A^\prime) | V \rangle
\end{align*},
$$

ここで $A^\prime$ は `bounds` を使用してスケーリングされた $A$ のバージョンです。もし $U$ と $V$ が行列であれば、次のように計算します。

$$
\begin{align*}
S & = \langle U | F(A^\prime) | V \rangle \\
  & = \frac{1}{N} \sum_{n=1}^N \sum_{m=1}^M \langle U_n | c_m T_m(A^\prime) | V_n \rangle
\end{align*},
$$

ここで $| U_n \rangle$ と $| V_n \rangle$ は各行列の列です。
