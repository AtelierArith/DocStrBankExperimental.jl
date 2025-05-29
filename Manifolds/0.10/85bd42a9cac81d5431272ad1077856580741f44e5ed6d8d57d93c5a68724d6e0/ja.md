```
get_coordinates(M::Rotations, p, X)
get_coordinates(M::OrthogonalMatrices, p, X)
get_coordinates(M::UnitaryMatrices, p, X)
```

点 `p` における [`Rotations`](@ref) $\mathrm{SO}(n)$ のユニークな接ベクトル成分 $X^i$ を、接ベクトルの行列表現 `X` から抽出します。

リー代数 $𝔰𝔬(n)$ の基底は、$\mathrm{SO}(2)$ の場合、$X^1 = θ = X_{21}$ が回転角であり、$\mathrm{SO}(3)$ の場合、$(X^1, X^2, X^3) = (X_{32}, X_{13}, X_{21}) = θ u$ が角速度と軸-角表現であるように選ばれます。ここで、$u$ は回転軸に沿った単位ベクトルです。

$$
n ≥ 4
$$

の場合の $\mathrm{SO}(n)$ では、$X^i$ の追加要素は $X^{j (j - 3)/2 + k + 1} = X_{jk}$ であり、$j ∈ [4,n], k ∈ [1,j)$ です。
