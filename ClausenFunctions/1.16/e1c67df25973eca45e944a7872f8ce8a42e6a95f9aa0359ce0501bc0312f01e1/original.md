```
cl(n, z)
```

Returns the value of the Clausen function $\operatorname{Cl}_n(z)$ for all integers $n\in\mathbb{Z}$ and arguments $z$ of type `Real` or `Complex`.  For complex $z\in\mathbb{C}$ this function is defined as

$$
\begin{aligned}
\operatorname{Cl}_n(z) &= \frac{i}{2}\left[\operatorname{Li}_n(e^{-iz}) - \operatorname{Li}_n(e^{iz})\right], \qquad \text{for}~n~\text{even}, \\
\operatorname{Cl}_n(z) &= \frac{1}{2}\left[\operatorname{Li}_n(e^{-iz}) + \operatorname{Li}_n(e^{iz})\right], \qquad \text{for}~n~\text{odd}.
\end{aligned}
$$

For real $z\in\mathbb{R}$ the function simplifies to

$$
\begin{aligned}
\operatorname{Cl}_n(z) &= \Im[\operatorname{Li}_n(e^{iz})] = \sum_{k=1}^\infty \frac{\sin(kz)}{k^n}, \qquad \text{for even}~n>0, \\
\operatorname{Cl}_n(z) &= \Re[\operatorname{Li}_n(e^{iz})] = \sum_{k=1}^\infty \frac{\cos(kz)}{k^n}, \qquad \text{for odd}~n>0.
\end{aligned}
$$

Note: $\operatorname{Cl}_1(z)$ is not defined for $z=2k\pi$ with $k\in\mathbb{Z}$.

For $z$ of type `Float16`, `Float32` or `Float64` the implementation follows the approach presented in [Jiming Wu, Xiaoping Zhang, Dongjie Liu, "An efficient calculation of the Clausen functions Cl_n(θ)(n >= 2)", Bit Numer Math 50, 193-206 (2010) [https://doi.org/10.1007/s10543-009-0246-8](https://doi.org/10.1007/s10543-009-0246-8)].

Author: Alexander Voigt

License: MIT

# Example

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
