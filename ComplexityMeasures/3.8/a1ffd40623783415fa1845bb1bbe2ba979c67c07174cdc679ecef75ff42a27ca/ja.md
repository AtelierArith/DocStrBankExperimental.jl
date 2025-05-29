```
StatisticalComplexity <: ComplexityEstimator
StatisticalComplexity(; kwargs...)
```

統計的複雑性とエントロピーの推定器で、元々は [Rosso2007](@cite) によって提案され、[Rosso2013](@citet) によって一般化されました。

私たちの実装は、任意の有効な距離メトリック、事前に知られた [`total_outcomes`](@ref) を持つ任意の [`OutcomeSpace`](@ref)、任意の [`ProbabilitiesEstimator`](@ref)、および任意の正規化可能な離散 [`InformationMeasure`](@ref) への一般化を拡張します。

[`complexity`](@ref) と共に使用されます。

## キーワード引数

  * `o::OutcomeSpace = OrdinalPatterns{3}()`. 入力データが離散化される方法を制御する [`OutcomeSpace`](@ref) です。
  * `pest::ProbabilitiesEstimator = RelativeAmount()`: 離散化された入力データに対して確率を推定するために使用される [`ProbabilitiesEstimator`](@ref) です。
  * `hest = Renyi()`: [`DiscreteInfoEstimator`](@ref) または [`InformationMeasure`](@ref) です。 [`information_maximum`](@ref) を定義する任意の情報測定がここで有効であり、エクストロピーを含みます。 推定器が指定されていない場合、[`PlugIn`](@ref) 推定器を使用して測定が推定されます。
  * `dist <: SemiMetric = JSDivergence()`: 推定された確率分布と同じ最大数の結果を持つ一様分布との間の距離を推定するために使用する距離測定（Distances.jl から）です。

## 説明

統計的複雑性は次のように定義されます。

$$
C_q[P] = \mathcal{H}_q\cdot \mathcal{Q}_q[P],
$$

ここで $Q_q$ は距離測定から得られる「不均衡」であり、$H_q$ は無秩序測定です。 元の論文 [Rosso2007](@cite) では、この複雑性測定は、[`OrdinalPatterns`](@ref) を使用して、情報測定として [`Shannon`](@ref) エントロピーを用い、距離測定としてジェンセン・シャノン発散を使用した順序パターンベースの確率分布を介して定義されました。

私たちの実装は、[Rosso2013](@citet) で開発された複雑性測定のさらなる一般化です。 $H_q$ を任意の正規化可能な [`InformationMeasure`](@ref)、例えば [`Shannon`](@ref)、[`Renyi`](@ref) または [`Tsallis`](@ref) エントロピーとし、$Q_q$ をユークリッド、ウータース、クルバック、q-クルバック、ジェンセンまたは q-ジェンセン距離のいずれかとします。

$$
Q_q[P] = Q_q^0\cdot D[P, P_e],
$$

ここで $D[P, P_e]$ は、得られた分布 $P$ と同じ最大数のビンを持つ一様分布との間の距離であり、距離測定 `dist` によって測定されます。

## 使用法

統計的複雑性は、選択された情報測定（通常はエントロピー）と組み合わせてのみ使用されます。 情報測定の推定値は、構造体の `Ref` 値としてアクセスできます。

```julia
x = randn(100)
c = StatisticalComplexity()
compl = complexity(c, x)
entr = first(entropy_complexity(c, x)) # 複雑性とエントロピーの両方の値
```

`complexity(c::StatisticalComplexity, x)` は統計的複雑性のみを返します。 エントロピー（または他の情報測定）の値と統計的複雑性の両方を `Tuple` として取得するには、ラッパー [`entropy_complexity`](@ref) を使用します。

関連情報: [`entropy_complexity_curves`](@ref). ```
