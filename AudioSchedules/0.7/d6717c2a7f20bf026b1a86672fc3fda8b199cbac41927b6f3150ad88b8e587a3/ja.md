```
make_series(synthesizer, sample_rate)
```

`synthesizer`を`sample_rate`（`Hz`のような周波数単位）で再生するイテレータを返します。イテレータは-1と1の間の`Float64`を生成する必要があります。イテレータはスケジュールされている間は決して終了しないと仮定します。
