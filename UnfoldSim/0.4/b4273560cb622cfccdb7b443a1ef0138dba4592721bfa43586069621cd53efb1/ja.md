```
LinearModelComponent <: AbstractComponent
```

1人の被験者のための重回帰コンポーネントです。

すべてのフィールドに名前を付けることができます。 [`SingleSubjectDesign`](@ref) と一緒に使用すると最適です。

# フィールド

  * `basis::Any`: アクセスされると「基底関数」を提供するオブジェクト、例えば `hanning(40)::Vector`、これは単一のイベントでの応答を定義します。モデルの予測によって重み付けされます。将来のバージョンでは関数を許可する予定ですが、v0.3の時点では配列のようなオブジェクトに制限されています。
  * `formula::Any`: StatsModels の `formula` オブジェクト、例えば `@formula 0 ~ 1 + cond`（左辺は必ず0でなければなりません）。
  * `β::Vector`: ベータ/係数のベクトルで、式に適合する必要があります。
  * `contrasts::Dict` (オプション): どのカテゴリ変数にどのコーディングスキームを使用するかを決定します。デフォルトは空で、これはダミーコーディングに対応します。詳細については [https://juliastats.org/StatsModels.jl/stable/contrasts](https://juliastats.org/StatsModels.jl/stable/contrasts) を参照してください。

# 例

```julia-repl
julia> LinearModelComponent(;
           basis = hanning(40),
           formula = @formula(0 ~ 1 + cond),
           β = [1., 2.],
           contrasts = Dict(:cond => EffectsCoding())
       )
LinearModelComponent
  basis: Array{Float64}((40,)) [0.0, 0.006474868681043577, 0.02573177902642726, 0.0572719871733951, 0.10027861829824952, 0.1536378232452003, 0.21596762663442215, 0.28565371929847283, 0.3608912680417737, 0.43973165987233853  …  0.43973165987233853, 0.3608912680417737, 0.28565371929847283, 0.21596762663442215, 0.1536378232452003, 0.10027861829824952, 0.0572719871733951, 0.02573177902642726, 0.006474868681043577, 0.0]
  formula: StatsModels.FormulaTerm{StatsModels.ConstantTerm{Int64}, Tuple{StatsModels.ConstantTerm{Int64}, StatsModels.Term}}
  β: Array{Float64}((2,)) [1.0, 2.0]
  contrasts: Dict{Symbol, EffectsCoding}
```

[`MixedModelComponent`](@ref) や [`MultichannelComponent`](@ref) も参照してください。
