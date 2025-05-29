```
sl(n, z)
```

すべての整数 $n\in\mathbb{Z}$ と `Real` または `Complex` 型の引数 $z$ に対して、Glaisher-Clausen 関数 $\operatorname{Sl}_n(z)$ の値を返します。複素数 $z\in\mathbb{C}$ に対して、この関数は次のように定義されます。

$$
\begin{aligned}
\operatorname{Sl}_n(z) &= \frac{1}{2}\left[\operatorname{Li}_n(e^{-iz}) + \operatorname{Li}_n(e^{iz})\right], \qquad \text{for}~n~\text{even}, \\
\operatorname{Sl}_n(z) &= \frac{i}{2}\left[\operatorname{Li}_n(e^{-iz}) - \operatorname{Li}_n(e^{iz})\right], \qquad \text{for}~n~\text{odd}.
\end{aligned}
$$

実数 $z\in\mathbb{R}$ に対して、この関数は次のように簡略化されます。

$$
\begin{aligned}
\operatorname{Sl}_n(z) &= \Re[\operatorname{Li}_n(e^{iz})] = \sum_{k=1}^\infty \frac{\cos(kz)}{k^n}, \qquad \text{for even}~n>0, \\
\operatorname{Sl}_n(z) &= \Im[\operatorname{Li}_n(e^{iz})] = \sum_{k=1}^\infty \frac{\sin(kz)}{k^n}, \qquad \text{for odd}~n>0.
\end{aligned}
$$

注意: 一貫性を保つために、$\operatorname{Sl}_1(0) = 0$ と設定します。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> sl(10, 1.0)
0.5398785706335891

julia> sl(10, big"1")
0.5398785706335893473201701431352733846690266746377581980285682505050227015352517

julia> sl(10, 1.0 + 1.0im)
0.832020890646937 - 0.9921163924162678im

julia> sl(10, big"1" + 1im)
0.832020890646937194384242195240640660735825609698824394209500978844042810286907 - 0.9921163924162683284596904585334878021171116435958891901780686447162617670776108im
```
