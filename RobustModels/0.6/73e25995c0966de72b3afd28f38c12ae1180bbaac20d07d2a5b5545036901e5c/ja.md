```
fit(
    ::Type{M},
    X::AbstractMatrix{T},
    y::AbstractVector{T},
    est::AbstractMEstimator;
    method::Symbol       = :auto,  # :chol, :qr, :cg
    dofit::Bool          = true,
    wts::FPVector        = similar(y, 0),
    offset::FPVector     = similar(y, 0),
    fitdispersion::Bool  = false,
    ridgeλ::Real         = 0,
    ridgeG::Union{UniformScaling, AbstractArray} = I,
    βprior::AbstractVector = [],
    quantile::Union{Nothing, AbstractFloat} = nothing,
    dropcollinear::Bool = false,
    initial_scale::Union{Symbol, Real}=:mad,
    σ0::Union{Nothing, Symbol, Real}=initial_scale,
    initial_coef::AbstractVector=[],
    β0::AbstractVector=initial_coef,
    correct_leverage::Bool=false,
    fitargs...,
) where {M<:RobustLinearModel, T<:AbstractFloat}
```

モデル行列（または式）Xと応答ベクトル（またはデータフレーム）yを使用して、ロバスト推定器を用いてロバストモデルを作成します。

# 引数

  * `X`: モデル行列（密行列または疎行列のいずれか）または式
  * `y`: 応答ベクトルまたはテーブル（データフレーム、ネームドタプルなど）。
  * `est`: ロバスト推定器

# キーワード

  * `method::Symbol = :auto`: 重み付き線形システムを解くために使用するメソッド、`chol`（デフォルト）、`qr`または`cg`。デフォルトメソッドを選択するには`:auto`を使用します；
  * `dofit::Bool = true`: falseの場合、フィッティングせずにモデルオブジェクトを返します；
  * `dropmissing::Bool = false`: trueの場合、欠損値を含む行を削除します（および非欠損型に変換します）。`dropmissing=true`の場合、観測数は入力配列のサイズよりも小さくなる可能性があります；
  * `wts::Vector = similar(y, 0)`: 観測の事前確率重み。重みが使用されない場合は空（長さ0）でもかまいません（デフォルト）；
  * `offset::Vector = similar(y, 0)`: オフセットベクトル、オフセットが使用されない場合は空であるべきです；
  * `fitdispersion::Bool = false`: 分散を再評価します；
  * `ridgeλ::Real = 0`: 正の場合、収縮パラメータ`ridgeλ`を持つロバストリッジ回帰を実行します。[`RidgePred`](@ref)オブジェクトが使用されます；
  * `ridgeG::Union{UniformScaling, AbstractArray} = I`: カスタム正則化行列を定義します。デフォルトは単位行列（切片のために0を持つ）です；
  * `βprior::AbstractVector = []`: リッジ回帰の係数のためのカスタム事前を定義します。デフォルトは`zeros(p)`です；
  * `quantile::Union{Nothing, AbstractFloat} = nothing`:   [`GeneralizedQuantileEstimator`](@ref)専用、推定する分位点を定義します；
  * `dropcollinear::Bool=false`: フルランク未満のモデル行列を受け入れるかどうかを制御します；
  * `contrasts::AbstractDict{Symbol,Any} = Dict{Symbol,Any}()`: 用語名（`Symbol`として）を用語タイプ（例：`ContinuousTerm`）またはコントラスト（例：`HelmertCoding()`、`SeqDiffCoding(; levels=["a", "b", "c"])`など）にマッピングする`Dict`。変数に対してコントラストが提供されていない場合、データ列のデータ型に基づいて適切な用語タイプが推測されます：数値データは連続であると仮定され、非数値データはカテゴリカルであると仮定されます（デフォルトのコントラストタイプは`DummyCoding()`です）；
  * `initial_scale::Union{Symbol, Real}=:mad`: 初期スケール推定、非凸推定器の場合、グローバル最小値を見つけるのに役立ちます。`:mad`、`L1`または`extrema`（ロバストでない）を使用した自動計算。
  * `σ0::Union{Nothing, Symbol, Real}=initial_scale`: `initial_scale`のエイリアス；
  * `initial_coef::AbstractVector=[]`: 初期係数推定、非凸推定器の場合、グローバル最小値を見つけるのに役立ちます。
  * `β0::AbstractVector=initial_coef`: `initial_coef`のエイリアス；
  * `correct_leverage::Bool=false`: [`leverage_weights`](@ref)を使用してレバレッジ補正重みを適用します。
  * `fitargs...`: IRLSアルゴリズムの収束を制御するために使用される他のキーワード引数（[`RobustModels.pirls!`](@ref）を参照）。

# 出力

ロバスト線形モデルオブジェクト。
