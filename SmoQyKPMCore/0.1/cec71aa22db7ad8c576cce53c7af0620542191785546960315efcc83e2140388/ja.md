```
kpm_dot(
    A, coefs::AbstractVector, bounds, R::T,
    tmp = zeros(eltype(R), size(R)..., 3)
) where {T<:AbstractVecOrMat}
```

もし $R$ が単一のベクトルであれば、内積を計算します。

$$
\begin{align*}
S & = \langle R | F(A^\prime) | R \rangle \\
  & = \sum_{m=1}^M \langle R | c_m T_m(A^\prime) | R \rangle
\end{align*},
$$

ここで $A^\prime$ は `bounds` を使用してスケーリングされた $A$ のバージョンです。もし $R$ が行列であれば、次のように計算します。

$$
\begin{align*}
S & = \langle R | F(A^\prime) | R \rangle \\
 & = \frac{1}{N} \sum_{n=1}^N \sum_{m=1}^M \langle R_n | c_m T_m(A^\prime) | R_n \rangle
\end{align*},
$$

ここで $| R_n \rangle$ は $R$ の列です。
