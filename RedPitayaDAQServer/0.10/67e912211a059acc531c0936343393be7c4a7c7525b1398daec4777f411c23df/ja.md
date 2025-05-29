```
calibDACOffset!(rp::RedPitaya, channel::Integer, val)
```

指定されたチャネルのキャリブレーションDACオフセット`val`をRedPitayaのEEPROMに保存します。この値は、出力電圧をオフセットするためにサーバーによって使用されます。絶対値は1.0 V未満でなければなりません。
