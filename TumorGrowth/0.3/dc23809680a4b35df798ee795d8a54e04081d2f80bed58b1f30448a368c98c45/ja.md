```
compare(times, volumes, models; holdouts=3, metric=mae, advanced_options...)
```

指定された患者の `times` と病変の `volumes` を使用して `models` をキャリブレーションし、最後の `holdouts` データポイントからなるホールドアウトセットを使用してそれらのモデルを比較します。

```julia
times = [0.1, 6.0, 16.0, 24.0, 32.0, 39.0]
volumes = [0.00023, 8.4e-5, 6.1e-5, 4.3e-5, 4.3e-5, 4.3e-5]

julia> comparison = compare(times, volumes, [gompertz, logistic])
ModelComparison with 3 holdouts:
  metric: mae
  gompertz:     2.198e-6
  logistic:     6.55e-6

julia> errors(comparison)
2-element Vector{Float64}:
 2.197843662660861e-6
 6.549858321487298e-6

julia> p = parameters(comparison)[1]  # calibrated parameter for `gompertz`
(v0 = 0.00022643603114569068, v∞ = 3.8453274218216947e-5, ω = 0.11537512108224635)

julia> gompertz(times, p)
6-element Vector{Float64}:
 0.00022643603114569068
 9.435316392754094e-5
 5.1039159299783234e-5
 4.303209015899451e-5
 4.021112910411027e-5
 3.922743006690166e-5
```

# 比較の視覚化

```julia
using Plots
plot(comparison, title="2つのモデルの比較")
```

# キーワードオプション

  * `holdouts=3`: キャリブレーションデータの最後から除外される時間-ボリュームペアの数
  * `metric=mae`: ホールドアウトセットに適用されるメトリック; ボリューム `v̂` を予測するモデルの報告された誤差は `metric(v̂, v)` であり、ここで `v` は `volumes` の最後の `holdouts` 値です。たとえば、StatisticalMeasures.jl の回帰測定をここで使用できます。組み込みのフォールバックは平均絶対誤差です。
  * `iterations=TumorGrowth.iterations.(models)`: `models` のキャリブレーションのための反復回数のベクトル
  * `calibration_options`: 各モデルの `CalibrationProblem` に対するキーワード引数を提供する名前付きタプルのベクトル。可能なキーは: `p0`, `lower`, `upper`, `frozen`, `learning_rate`, `optimiser`, `radius`, `scale`, `half_life`, `penalty`、および任意のODEソルバーオプションに対応するキーです。指定されていないキーはデフォルトにフォールバックします。これらは [`CalibrationProblem`](@ref) ドキュメント文字列で説明されています。

[`errors`](@ref) や [`parameters`](@ref) も参照してください。
