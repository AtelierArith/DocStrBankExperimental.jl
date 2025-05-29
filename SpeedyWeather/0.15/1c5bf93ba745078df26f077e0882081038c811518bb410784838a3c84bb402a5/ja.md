```julia
initialize!(
    scheduler::SpeedyWeather.Schedule,
    clock::SpeedyWeather.Clock
) -> SpeedyWeather.Schedule

```

スケジュールを初期化します（初期化されていると仮定されるクロックを使用）。scheduler.every と scheduler.times の両方を考慮に入れ、周期的なものとイベントの両方を同時にスケジュールできます。ただし、特定の時間ステップで重なる場合、実行は一度だけ行われます。
