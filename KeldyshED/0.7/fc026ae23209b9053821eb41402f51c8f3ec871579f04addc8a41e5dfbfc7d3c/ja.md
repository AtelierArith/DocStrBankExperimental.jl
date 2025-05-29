```julia
reduced_density_matrix(
    ed::KeldyshED.EDCore,
    target_soi::KeldyshED.Hilbert.SetOfIndices,
    β::Real
) -> Any

```

平衡密度行列を計算します

$$
\hat\rho_{target} = \mathrm{Tr}_{env}[e^{-\beta\hat H}] / Z
$$

逆温度 $\beta$ で。

ハミルトニアン $\hat H$ は [`Hilbert spaces`](@ref KeldyshED.Hilbert.FullHilbertSpace) の直積 $H_{target} \otimes H_{env}$ で作用し、結果として得られる縮小行列は、[`set of indices`](@ref KeldyshED.Hilbert.SetOfIndices) `target_soi` によって生成されるすべてのフェルミオンフォック状態で張られた $H_{target}$ で作用します。
