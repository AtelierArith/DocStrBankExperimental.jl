```
scalarlogiset(dataset, features; kwargs...)
```

変数を持つデータセット構造をスカラー値の特徴を持つログセットに変換します。`dataset`が準拠すべきインターフェースについては、[`islogiseed`](@ref)を参照してください。

# 引数

  * `dataset`: ログセットに変換されるデータセット。[`islogiseed`](@ref)インターフェースに準拠している必要があります；
  * `features`: `dataset`の列に対応する特徴のベクトル；

# キーワード引数

  * `use_onestep_memoization::Union{Bool,Type{<:AbstractOneStepMemoset}}=!isnothing(conditions) && !isnothing(relations)`:

特定のスカラー条件と関係を使用して特定の短い式のチェックを最適化するために、ワンステップメモ化を有効にします（[`AbstractOneStepMemoset`](@ref）を参照）；

  * `conditions::Union{Nothing,AbstractVector{<:AbstractCondition}}=nothing`:

ワンステップメモ化に使用される条件またはメタ条件のセット。提供されない場合、各変数に適用される最小値と最大値によって与えられるメタ条件が使用されます（[`ScalarMetaCondition`](@ref）を参照）；

  * `relations::Union{Nothing,AbstractVector{<:AbstractRelation}}=nothing`:

ワンステップメモ化に使用される関係のセット（[`AbstractRelation`](@ref）を参照）；

  * `onestep_precompute_globmemoset::Bool = (use_onestep_memoization != false)`:

グローバルワンステップ式のメモ化セットを事前計算します。これは通常、少しの時間しかかかりません：実際、グローバル式は基礎付けられているため、中間の`check`結果は世界の数に依存しません。

  * `onestep_precompute_relmemoset::Bool = false`:

グローバルワンステップ式のメモ化セットを事前計算します。これは、関係と世界の数に応じて長い時間がかかる場合があります；通常は必要ありません。

  * `use_full_memoization::Union{Bool,Type{<:Union{AbstractOneStepMemoset,AbstractFullMemoset}}}=true`:

すべての中間`check`結果がキャッシュされて再計算を避けるフルメモ化を有効にします。これはワンステップメモ化と併用できます；

  * `print_progress::Bool = false`: 進行状況バーを表示します；
  * `allow_propositional::Bool = false`: 表形式（すなわち、非関係的）データセットを`PropositionalLogiset`としてインスタンス化することを許可します。モーダルログセットではなく；
  * `force_i_variables::Bool = false`: 条件が推論される場合（`conditions = nothing`）、(メタ)条件が利用可能な場合は`Symbol`名ではなく整数インデックスで変数を参照するように強制します（`varnames`を通じて、[`islogiseed`](@ref）を参照）。

# ロギシード特有のキーワード引数

  * `worldtype_by_dim::AbstractDict{<:Integer,<:Type} = Dict([0 => OneWorld, 1 => Interval, 2 => Interval2D])`:

データセットが[`MultiData.AbstractDimensionalDataset`](@ref)である場合、この[`dimensionality`](@ref)と希望する[`AbstractWorld`](@ref)タイプとのマップがフレームタイプを推測するために使用されます。デフォルトでは、次元性0、1、2の次元データセットは、それぞれOneWorld、Interval、およびInterval2Dに基づいてログセットを生成します。

# 例

```julia>repl
julia> df = DataFrame(A = [36, 37, 38], B = [1, 2, 3])
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │    36      1
   2 │    37      2
   3 │    38      3

julia> scalarlogiset(df; worldtype_by_dim=([0=>OneWorld]))
SupportedLogiset with 1 support (2.21 KBs)
├ worldtype:                   OneWorld
├ featvaltype:                 Int64
├ featuretype:                 VariableValue
├ frametype:                   SoleLogics.FullDimensionalFrame{0, OneWorld}
├ # instances:                 3
├ usesfullmemo:                true
├[BASE] UniformFullDimensionalLogiset of dimensionality 0 (688.0 Bytes)
│ ├ size × eltype:              (3, 2) × Int64
│ └ features:                   2 -> VariableValue[V1, V2]
└[SUPPORT 1] FullMemoset (0 memoized values, 1.5 KBs))
```

julia> pointlogiset = scalarlogiset(     X*df;     worldtype*by_dim=Dict([1 => SoleLogics.Point1D, 2 => SoleLogics.Point2D]) )

他にも[`AbstractModalLogiset`](@ref)、[`AbstractOneStepMemoset`](@ref)、`SoleLogics.AbstractRelation`、`SoleLogics.AbstractWorld`、[`ScalarCondition`](@ref)、[`VarFeature`](@ref)を参照してください。 ```
