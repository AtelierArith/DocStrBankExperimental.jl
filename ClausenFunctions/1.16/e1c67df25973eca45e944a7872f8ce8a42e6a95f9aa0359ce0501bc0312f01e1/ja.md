```
cl(n, z)
```

すべての整数 $n\in\mathbb{Z}$ と `Real` または `Complex` 型の引数 $z$ に対して、Clausen 関数 $\operatorname{Cl}_n(z)$ の値を返します。複素数 $z\in\mathbb{C}$ に対して、この関数は次のように定義されます。

$$
\begin{aligned}
\operatorname{Cl}_n(z) &= \frac{i}{2}\left[\operatorname{Li}_n(e^{-iz}) - \operatorname{Li}_n(e^{iz})\right], \qquad \text{for}~n~\text{even}, \\
\operatorname{Cl}_n(z) &= \frac{1}{2}\left[\operatorname{Li}_n(e^{-iz}) + \operatorname{Li}_n(e^{iz})\right], \qquad \text{for}~n~\text{odd}.
\end{aligned}
$$

実数 $z\in\mathbb{R}$ に対して、この関数は次のように簡略化されます。

$$
\begin{aligned}
\operatorname{Cl}_n(z) &= \Im[\operatorname{Li}_n(e^{iz})] = \sum_{k=1}^\infty \frac{\sin(kz)}{k^n}, \qquad \text{for even}~n>0, \\
\operatorname{Cl}_n(z) &= \Re[\operatorname{Li}_n(e^{iz})] = \sum_{k=1}^\infty \frac{\cos(kz)}{k^n}, \qquad \text{for odd}~n>0.
\end{aligned}
$$

注意: $\operatorname{Cl}_1(z)$ は $z=2k\pi$ で定義されていません ($k\in\mathbb{Z}$)。

`Float16`、`Float32` または `Float64` 型の $z$ に対して、実装は [Jiming Wu, Xiaoping Zhang, Dongjie Liu, "An efficient calculation of the Clausen functions Cl_n(θ)(n >= 2)", Bit Numer Math 50, 193-206 (2010) [https://doi.org/10.1007/s10543-009-0246-8](https://doi.org/10.1007/s10543-009-0246-8)] で示されたアプローチに従います。

著者: Alexander Voigt

ライセンス: MIT

# 例

```jldoctest; setup = :(using ClausenFunctions), output = false
julia> cl(10, 1.0)
0.8423605391686301

julia> cl(10, big"1")
0.8423605391686302305168624869816554653186479602725762955247227248477087749849797

julia> cl(10, 1.0 + 1.0im)
1.301796548970136 + 0.6333106255561783im

julia> cl(10, big"1" + 1im)
1.301796548970136401486390838171927382622047488046695826621336318796926878116022 + 0.6333106255561785282041229828047700199791464296534659278461150656661132141323808im
```
