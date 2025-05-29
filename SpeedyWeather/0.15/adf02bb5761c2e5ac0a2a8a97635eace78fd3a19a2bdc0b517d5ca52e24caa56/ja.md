```julia
Schedule(times::Dates.DateTime...) -> SpeedyWeather.Schedule

```

DateTime引数に基づくスケジュール。2つの連続した時間ステップi, i+1について、イベントは(i,i+1]の間に発生するときにi+1にスケジュールされます。
