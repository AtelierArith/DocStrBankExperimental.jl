```
calibDACLowerLimit!(rp::RedPitaya, channel::Integer)
```

指定されたチャネルのキャリブレーションDAC下限値`val`をRedPitayaのEEPROMに保存します。この値は、サーバーが出力電圧を制限するために使用されます。
