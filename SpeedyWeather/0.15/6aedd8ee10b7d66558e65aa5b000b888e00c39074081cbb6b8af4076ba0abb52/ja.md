```julia
initialize!(
    L::SpeedyWeather.Leapfrog,
    model::SpeedyWeather.AbstractModel
)

```

`L`を初期化するには、`model.output`からの出力時間ステップ`output_dt`を考慮してタイムステップを再計算します。再計算により、タイムステップがわずかに調整され、整数のタイムステップ数が出力時間ステップと正確に一致するようになります。
