```
inv_IpA!(G::AbstractMatrix{T}, A::LDR{T,E}, ws::LDRWorkspace{T,E})::Tuple{E,T} where {T,E}
```

数値的に安定した逆行列 $G := [I + A]^{-1}$ を計算します。ここで、$G$ は行列であり、$A$ は [`LDR`](@ref) 因子分解によって表されます。このメソッドはまた、$\log( \vert \det G\vert )$ と $\textrm{sign}(\det G)$ を返します。

# アルゴリズム

数値的に安定した逆行列 $G := [I + A]^{-1}$ は次の手順を用いて計算されます。

$$
\begin{align*}
G:= & [I+A]^{-1}\\
= & [I+L_{a}D_{a}R_{a}]^{-1}\\
= & [I+L_{a}D_{a,\min}D_{a,\max}R_{a}]^{-1}\\
= & [(R_{a}^{-1}D_{a,\max}^{-1}+L_{a}D_{a,\min})D_{a,\max}R_{a}]^{-1}\\
= & R_{a}^{-1}D_{a,\max}^{-1}[\overset{M}{\overbrace{R_{a}^{-1}D_{a,\max}^{-1}+L_{a}D_{a,\min}}}]^{-1}\\
= & R_{a}^{-1}D_{a,\max}^{-1}M^{-1},
\end{align*}
$$

ここで、$D_{a,\min} = \min(D_a, 1)$ および $D_{a,\max} = \max(D_a, 1)$ です。中間の行列の逆行列と関連する行列式の計算は、部分ピボットを用いたLU因子分解によって行われます。
