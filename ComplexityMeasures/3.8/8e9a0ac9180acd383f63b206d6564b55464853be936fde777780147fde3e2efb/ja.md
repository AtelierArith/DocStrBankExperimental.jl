```
MissingDispersionPatterns <: ComplexityEstimator
MissingDispersionPatterns(o = Dispersion()) → mdp
```

欠損分散パターン（MDP）の推定器であり、時系列の非線形性を検出するために使用できる複雑性測定値です [Zhou2023](@cite)。

[`complexity`](@ref) または [`complexity_normalized`](@ref) と共に使用されます。

## 説明

[`complexity`](@ref) と共に使用されると、`complexity(mdp)` は単に [`missing_outcomes`](@ref)`(o)` と文法的に同等です。[`complexity_normalized`](@ref) と共に使用されると、正規化は単に `missing_outcomes(o)/total_outcomes(o)` です。

!!! note "エンコーディング"
    [`Dispersion`](@ref) のCDFから整数への線形マッピングは、区間 `[0, 1]` の等間隔分割に基づいています。これは、線形マッピング $s_i := \text{round}(y + 0.5)$ を使用する [Zhou2023](@citet) とは少し異なります。


## 使用法

[Zhou2023](@citet) では、[`MissingDispersionPatterns`](@ref) が時系列 `x` のMDPを `x` のサロゲートのアンサンブルの値と比較することによって、時系列の非線形性を検出するために使用されます。これは、[TimeseriesSurrogates.jl](https://github.com/JuliaDynamics/TimeseriesSurrogates.jl) の標準分析に従います。$x$ のMDP値がサロゲート分布の高い分位数のいくつかよりも有意に大きい場合、それは非線形性の証拠と見なされます。

関連情報: [`Dispersion`](@ref), [`ReverseDispersion`](@ref), [`total_outcomes`](@ref)。
