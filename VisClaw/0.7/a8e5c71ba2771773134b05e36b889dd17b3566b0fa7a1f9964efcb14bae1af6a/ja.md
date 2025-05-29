```
replaceunit!(fgmax::VisClaw.FGmax, unit::Symbol)
replaceunit!(gauge::VisClaw.Gauge, unit::Symbol)
replaceunit!(amrs::VisClaw.AMR, unit::Symbol)
replaceunit!(track::VisClaw.Track, unit::Symbol)
```

時間単位コンバータ 第二引数 unit は :second, :minute, :hour, または :day のいずれかでなければなりません。
