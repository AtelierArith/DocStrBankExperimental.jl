```
function SmoothArcLengthInterpolation(
    u::AbstractMatrix,
    d::AbstractMatrix
    [, make_intersections::Val{<:Bool}];
    shape_itp::Union{AbstractInterpolation, Nothing} = nothing,
    extrapolation::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_left::ExtrapolationType.T = ExtrapolationType.None,
    extrapolation_right::ExtrapolationType.T = ExtrapolationType.None,
    cache_parameters::Bool = false,
    assume_linear_t = 1e-2,
    in_place::Bool = true)
```

与えられたデータと与えられた接線を使用して、線分と円弧を用いたC¹滑らかな単位速度補間を行います。

## 引数

  * `u`: 行列形式で補間されるデータ; (ndim, ndata)。
  * `d`: 点 `u` における曲線の接線。
  * `make_intersections`: 連続する（接線）線が交差することを保証するために、提供されたデータの間に追加の（点、接線）ペアを追加する必要があるかどうか。デフォルトは `Val(true)` です。

## キーワード引数

  * `shape_itp`: 存在する場合、近似されている補間。注意すべきは、この補間は使用されず、`SmoothArcLengthInterpolation` の形状がどこから来たのかを追跡するために渡されるだけです。
  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは `ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic` および `ExtrapolationType.Reflective` です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては `extrapolation` を参照してください。このキーワードは `extrapolation != Extrapolation.none` の場合は無視されます。
  * `assume_linear_t`: 均等に分布した横軸に対してより速いインデックス検索動作を指定するためのブール値。あるいは、直線に対する差の正規化された標準偏差に基づくテストのために数値的な閾値を指定することもできます（[`looks_linear`](@ref) を参照）。デフォルトは 1e-2 です。

```
