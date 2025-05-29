```
calibADCOffset!(rp::RedPitaya, channel::Integer, val)
```

指定されたチャネルのキャリブレーションADCオフセット`val`をRedPitayaのEEPROMに保存します。絶対値は1.0 V未満でなければなりません。

関連情報として、[convertSamplesToPeriods!](@ref)、[convertSamplesToFrames](@ref)を参照してください。
