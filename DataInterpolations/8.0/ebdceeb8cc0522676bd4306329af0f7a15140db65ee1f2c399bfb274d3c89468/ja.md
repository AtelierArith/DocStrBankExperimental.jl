```
 SmoothArcLengthInterpolation(
    u::AbstractMatrix{U};
    t::Union{AbstractVector, Nothing} = nothing,
    interpolation_type::Type{<:AbstractInterpolation} = QuadraticSpline,
    kwargs...) where {U}
```

データを単位速度でC¹滑らかに補間し、線分と円弧で補間（形状補間）を近似します。

## 引数

  * `u`: 行列形式の補間対象データ; (ndim, ndata)。

注意: このメソッドでは、形状補間のコンストラクタにキーワード引数を渡すことはできません。これを行いたい場合は、形状補間を自分で構築し、`SmoothArcLengthInterpolation(shape_itp::AbstractInterpolation; kwargs...)` メソッドを使用してください。

## キーワード引数

  * `t`: 形状補間の時間点。デフォルトでは、点 `u` の間のユークリッド距離の累積和によって与えられます。
  * `interpolation_type`: 形状補間のタイプ。デフォルトは `QuadraticSpline` です。`SmoothArcLengthInterpolation` がC¹滑らかであるためには、`interpolation_type` もC¹滑らかでなければなりません。
  * `m`: 時間点間の各区間で形状補間が評価される点の数。`SmoothArcLengthInterpolation` は m → ∞ のとき形状補間（形状）に収束します。
  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは `ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic` および `ExtrapolationType.Reflective` です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `assume_linear_t`: 均等に分布したアブシッサに対してより高速なインデックス検索動作を指定するためのブール値。あるいは、直線に対する差の正規化された標準偏差に基づくテストのために数値的な閾値を指定することもできます（[`looks_linear`](@ref) を参照）。デフォルトは 1e-2 です。

```
