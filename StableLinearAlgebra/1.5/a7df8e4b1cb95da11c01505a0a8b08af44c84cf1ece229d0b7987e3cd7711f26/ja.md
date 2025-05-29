```
inv_IpUV!(G::AbstractMatrix{T}, U::LDR{T,E}, V::LDR{T,E}, ws::LDRWorkspace{T,E})::Tuple{E,T} where {T,E}
```

数値的に安定した逆行列 $G := [I + UV]^{-1}$ を計算します。ここで、$G$ は行列であり、$U$ と $V$ は [`LDR`](@ref) 分解によって表されます。このメソッドはまた、$\log( \vert \det G\vert )$ と $\textrm{sign}(\det G)$ を返します。

# アルゴリズム

数値的に安定した逆行列 $G := [I + UV]^{-1}$ は次の手順を用いて計算されます。

$$
\begin{align*}
G:= & [I+UV]^{-1}\\
= & [I+L_{u}D_{u}R_{u}L_{v}D_{v}R_{v}]^{-1}\\
= & [I+L_{u}D_{u,\max}D_{u,\min}R_{u}L_{v}D_{v,\min}D_{v,\max}R_{v}]^{-1}\\
= & [L_{u}D_{u,\max}(D_{u,\max}^{-1}L_{u}^{\dagger}R_{v}^{-1}D_{v,\max}^{-1}+D_{u,\min}R_{u}L_{v}D_{v,\min})D_{v,\max}R_{v}]^{-1}\\
= & R_{v}^{-1}D_{v,\max}^{-1}[\overset{M}{\overbrace{D_{u,\max}^{-1}L_{u}^{\dagger}R_{v}^{-1}D_{v,\max}^{-1}+D_{u,\min}R_{u}L_{v}D_{v,\min}}}]^{-1}D_{u,\max}^{-1}L_{u}^{\dagger}\\
= & R_{v}^{-1}D_{v,\max}^{-1}M^{-1}D_{u,\max}^{-1}L_{u}^{\dagger}
\end{align*}
$$

中間の行列の逆行列と関連する行列式の計算は、部分ピボットを用いたLU分解によって行われます。
