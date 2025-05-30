与えられた散乱行列（6つの独立した列：a1, a2, a3, a4, b1, b2）を一般球面関数（GSF）係数に展開します。

```julia
expand(
    F,
    θ₀;
    smax,
    smin,
    ngauss,
    double_threshold,
    adding_step,
    stop_threshold,
    cutoff,
    interpolation_strategy,
    ε,
    θₑ,
    error_type,
    _kwargs...
)

```

  * `F`: 散乱行列の列で、`Nθ x 6` の行列である必要があります。
  * `θ₀`: 散乱角度。最大値が `π` より大きい場合、角度は度数法であると仮定され、それ以外の場合はラジアンであると仮定されます。

オプションのパラメータ：

  * `smax`: 展開の最高レベル。デフォルトは `-1` で、その場合、最高レベルは試行錯誤によって、所望の精度（`ε` と `error_type` で定義される）に達するまで決定されます。
  * `smin`: 反復の開始点。デフォルトは `30` です。
  * `ngauss`: ガウス求積点の数を決定する関数。現在の展開レベルに `+1`、すなわち `s + 1` を入力として取ります。デフォルトは `identity` です。
  * `double_threshold`: `s` が毎回倍増される最高レベル。デフォルトは `5000` です。
  * `adding_step`: 追加フェーズでのステップサイズ。デフォルトは `100` です。
  * `stop_threshold`: 許可される最高の展開レベル。デフォルトは `20000` です。
  * `interpolation_strategy`: 補間戦略。デフォルトは `PolarizedBRF.Linear` で、`Interpolations.jl` の `LinearInterpolation` を使用します。オプションとして `PolarizedBRF.Spline` があり、`Dierckx.jl` の `Spline1D` を使用します。
  * `cutoff`: このレベルでの `α₁` の絶対値が `cutoff` より小さい場合に展開係数をカットオフします。デフォルトは `0.0` で、カットオフは適用されません。Ito et al. (2018) は `cutoff = 1e-8` を使用しました。
  * `ε`: 所望の誤差境界。デフォルトは `0.02` です。
  * `θₑ`: 誤差チェックに使用される角度。デフォルトは `θ₀` です。
  * `error_type`: 誤差の種類。デフォルトは `PolarizedBRF.AbsoluteError` で、他のオプションには `PolarizedBRF.RelativeError` と `PolarizedBRF.RootMeanSquaredError` が含まれます。
