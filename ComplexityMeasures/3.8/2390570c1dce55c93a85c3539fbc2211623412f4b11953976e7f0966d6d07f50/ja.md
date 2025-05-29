```
Shrinkage{<:OutcomeSpace} <: ProbabilitiesEstimator
Shrinkage(; t = nothing, λ = nothing)
```

`Shrinkage`推定量は、与えられた`m`要素のカウントベースの[`OutcomeSpace`](@ref)上で確率を推定するために、[`probabilities`](@ref)および関連関数と共に使用され、James-Stein型のシュリンク[JamesStein1992](@cite)を使用します。これは[Hausser2009](@citet)で提示されています。

## 説明

`Shrinkage`推定量は、セル確率$\theta_{k}^{\text{Shrink}}$を次のように推定します。

$$
\theta_{k}^{\text{Shrink}} = \lambda t_k + (1-\lambda) \hat{\theta}_k^{RelativeAmount},
$$

ここで、$\lambda \in [0, 1]$はシュリンクの強度（$\lambda = 0$はシュリンクなし、$\lambda = 1$は完全なシュリンクを意味します）、$t_k$はシュリンクターゲットです。[Hausser2009](@citet)は$t_k = 1/m$、すなわち一様分布を選択します。

`t == nothing`の場合、すべての$k$に対して$t_k$は$1/m$に設定されます。これは[Hausser2009](@citet)と同様です。`λ == nothing`（デフォルト）の場合、シュリンクの強度は[Hausser2009](@citet)に従って最適化されます。したがって、何をしているのか分からない限り、手動で`λ`や`t`を選択しない方が良いでしょう。

## 仮定

`Shrinkage`推定量は、固定された既知の結果の数`m`を仮定します。したがって、[`probabilities_and_outcomes`](@ref)および[`allprobabilities_and_outcomes`](@ref)と共に使用すると、入力データで全ての結果が観測されているかどうかに応じて異なる結果が得られます。[`probabilities_and_outcomes`](@ref)の場合、`m`は*観測された*結果の数です。[`allprobabilities_and_outcomes`](@ref)の場合、`m = total_outcomes(o, x)`であり、ここで`o`は[`OutcomeSpace`](@ref)で、`x`は入力データです。

!!! note
    [`allprobabilities_and_outcomes`](@ref)と共に使用される場合、観測されていない結果に非ゼロの確率が割り当てられることがあります。これは、例えば[`missing_outcomes`](@ref)を使用する場合に結果に影響を与える可能性があります。


## 例

```julia
using ComplexityMeasures
x = cumsum(randn(100))
ps_shrink = probabilities(Shrinkage(), OrdinalPatterns{3}(), x)
```

関連情報: [`RelativeAmount`](@ref), [`BayesianRegularization`](@ref).
