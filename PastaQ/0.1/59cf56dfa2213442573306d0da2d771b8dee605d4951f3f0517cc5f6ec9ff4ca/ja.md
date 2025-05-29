```
getsamples(M::Union{MPS,MPO}, nshots::Int; kwargs...)
getsamples(T::ITensor, nshots::Int)
```

波動関数 $|\psi\rangle$ または密度演算子 $\rho$ に対して、MPS/MPO 参照基底で `nshots` の射影測定を行います。各測定は、確率分布から引かれた二項ベクトル $\sigma = (\sigma_1,\sigma_2,\dots)$ で構成されます：

  * $$
    P(\sigma) = |\langle\sigma|\psi\rangle|^2
    $$

    、   もし $M = |\psi\rangle$ が `MPS` の場合。
  * $$
    P(\sigma) = \langle\sigma|\rho|\sigma\rangle
    $$

    :  もし $M = \rho$ が `MPO` の場合。
