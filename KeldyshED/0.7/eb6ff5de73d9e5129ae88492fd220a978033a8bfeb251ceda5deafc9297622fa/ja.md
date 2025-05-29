```julia
reduced_evolution_operator(
    ed::KeldyshED.EDCore,
    target_soi::KeldyshED.Hilbert.SetOfIndices,
    grid::Keldysh.AbstractTimeGrid
) -> Keldysh.GenericTimeGF{ComplexF64}

```

与えられたコンター時間グリッド上で、縮小進化演算子を計算します。

$$
\hat S_{target}(t, t') =
\mathrm{Tr}_{env}\left[\exp\left(-i \int_{t'}^{t} \hat H d\bar t\right)\right]
$$

ハミルトニアン $\hat H$ は、[`ヒルベルト空間`](@ref KeldyshED.Hilbert.FullHilbertSpace) $H_{target} \otimes H_{env}$ の直積で作用し、結果として得られる縮小進化演算子は、[`インデックスの集合`](@ref KeldyshED.Hilbert.SetOfIndices) `target_soi` によって生成されるすべてのフェルミオンフォック状態により張られる $H_{target}$ で作用します。
