```
MixedModelComponent <: AbstractComponent
```

線形混合モデル（LMM）に従ってパラメータ間に階層的関係を追加するコンポーネントで、`MixedModels.jl`を介して定義されます。

すべてのフィールドに名前を付けることができます。 [`MultiSubjectDesign`](@ref)と一緒に使用すると最適です。

# フィールド

  * `basis::Any`: アクセスされると「基底関数」を提供するオブジェクト、例えば `hanning(40)::Vector`、これは単一のイベントでの応答を定義します。モデルの予測によって重み付けされます。将来のバージョンでは関数を許可する予定ですが、v0.3の時点では配列のようなオブジェクトに制限されています。
  * `formula::Any`: MixedModels.jlスタイルのフォーミュラオブジェクト、例えば `@formula 0 ~ 1 + cond + (1|subject)`。左辺は無視されます。
  * `β::Vector`: ベータ（固定効果）のベクトルで、フォーミュラに適合する必要があります。
  * `σs::Dict`: ランダム効果の分散の辞書、例えば `Dict(:subject => [0.5, 0.4])` または相関行列を指定するための `Dict(:subject=>[0.5,0.4,I(2,2)],...)`。技術的には、これはMixedModels.jlの `create_re` 関数に渡され、θ行列を作成します。
  * `contrasts::Dict`（オプション）: MixedModels.jlスタイルの辞書。どのカテゴリ変数にどのコーディングスキームを使用するかを決定します。デフォルトは空で、ダミーコーディングに対応します。詳細については [https://juliastats.org/StatsModels.jl/stable/contrasts](https://juliastats.org/StatsModels.jl/stable/contrasts) を参照してください。

# 例

```julia-repl
julia> MixedModelComponent(;
           basis = hanning(40),
           formula = @formula(0 ~ 1 + cond + (1 + cond|subject)),
           β = [1., 2.],
           σs= Dict(:subject => [0.5, 0.4]),
           contrasts=Dict(:cond => EffectsCoding())
       )
MixedModelComponent
  basis: Array{Float64}((40,)) [0.0, 0.006474868681043577, 0.02573177902642726, 0.0572719871733951, 0.10027861829824952, 0.1536378232452003, 0.21596762663442215, 0.28565371929847283, 0.3608912680417737, 0.43973165987233853  …  0.43973165987233853, 0.3608912680417737, 0.28565371929847283, 0.21596762663442215, 0.1536378232452003, 0.10027861829824952, 0.0572719871733951, 0.02573177902642726, 0.006474868681043577, 0.0]
  formula: StatsModels.FormulaTerm{StatsModels.ConstantTerm{Int64}, Tuple{StatsModels.ConstantTerm{Int64}, StatsModels.Term, StatsModels.FunctionTerm{typeof(|), Vector{StatsModels.AbstractTerm}}}}
  β: Array{Float64}((2,)) [1.0, 2.0]
  σs: Dict{Symbol, Vector{Float64}}
  contrasts: Dict{Symbol, EffectsCoding}
```

他に [`LinearModelComponent`](@ref)、[`MultichannelComponent`](@ref) も参照してください。
