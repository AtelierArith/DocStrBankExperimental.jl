```
fit(ts,Δ;model::Type{<:TimeSeriesModel},x₀,lowerΩcutoff,upperΩcutoff,x_lowerbounds,x_upperbounds,method,taper)
fit(timeseries::TimeSeries;model::Type{<:TimeSeriesModel},x₀,lowerΩcutoff,upperΩcutoff,x_lowerbounds,x_upperbounds,method,taper)
```

`IPNewton` メソッドを使用して時系列モデルをフィットします。

# 引数

  * `ts`: 時系列を含む `n` 行 `D` 列の行列（または `D=1` の場合はベクトル）、ここで `n` は観測数、`D` は系列数です。
  * `Δ`: サンプリングレートで、正の実数である必要があります。
  * `timeseries`: `ts` と `Δ` の代わりに提供できます。
  * `model`: フィットされるモデル。モデルの実現ではなく、型である必要があります。例: JONSWAP{k} ではなく JONSWAP{K}(x)。
  * `x₀`: 初期パラメータの推測。
  * `lowerΩcutoff`: フィッティングに使用される周波数範囲の下限カットオフ。デフォルトは `0` です。
  * `upperΩcutoff`: フィッティングに使用される周波数範囲の上限カットオフ。デフォルトは `Inf` です。
  * `x_lowerbounds`: パラメータ空間の下限。`nothing` が提供される場合（デフォルト）、これらはモデルに基づいてデフォルト値に設定されます。
  * `x_upperbounds`: パラメータ空間の上限。`nothing` が提供される場合（デフォルト）、これらはモデルに基づいてデフォルト値に設定されます。
  * `method`: `:Whittle` または `:debiasedWhittle` のいずれか。
  * `taper`: 使用するテーパリングの選択。これは `nothing`（この場合、テーパリングは使用されません）または `dpss_nw` で、ここで `nw` は時間帯域幅の積です（詳細は DSP.dpss を参照してください）。
  * `options`: `Optim.Options` 型の最適化オプション。
