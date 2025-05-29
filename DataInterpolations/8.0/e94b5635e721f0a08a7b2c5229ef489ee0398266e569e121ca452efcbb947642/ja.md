```
function SmoothArcLengthInterpolation(
        shape_itp::AbstractInterpolation;
        m::Integer = 2,
        kwargs...)
```

`shape_itp`を線分と円弧を使用したC¹単位速度補間で近似します。

## 引数

  * `shape_itp`: 近似される補間。`SmoothArcLengthInterpolation`がC¹滑らかであるためには、`shape_itp`もC¹滑らかである必要があります。

## キーワード引数

  * `m`: 時間点間の各区間で形状補間が評価されるポイントの数。`SmoothArcLengthInterpolation`はm → ∞のときに形状補間（形状において）に収束します。
  * `extrapolation`: データの左側と右側に適用される外挿タイプ。可能なオプションは`ExtrapolationType.None`（デフォルト）、`ExtrapolationType.Constant`、`ExtrapolationType.Linear`、`ExtrapolationType.Extension`、`ExtrapolationType.Periodic`、および`ExtrapolationType.Reflective`です。
  * `extrapolation_left`: データの左側に適用される外挿タイプ。可能なオプションについては`extrapolation`を参照してください。このキーワードは`extrapolation != Extrapolation.none`の場合は無視されます。
  * `extrapolation_right`: データの右側に適用される外挿タイプ。可能なオプションについては`extrapolation`を参照してください。このキーワードは`extrapolation != Extrapolation.none`の場合は無視されます。
  * `assume_linear_t`: 均等に分布したアブシッサに対してより高速なインデックスルックアップ動作を指定するためのブール値。あるいは、直線に対する差の正規化された標準偏差に基づくテストのために数値的な閾値を指定することもできます（[`looks_linear`](@ref）を参照）。デフォルトは1e-2です。

```
