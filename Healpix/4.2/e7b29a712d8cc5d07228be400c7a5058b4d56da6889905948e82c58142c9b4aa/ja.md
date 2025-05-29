```
ang2pixNest(resol::Resolution, theta, phi) -> Integer
```

与えられた座標（`theta`、コラティチュード、`phi`、経度）を持つ点を含むピクセルのインデックスを返します。これは、ネストされた順序でピクセルを持つHealpixマップ用です。ピクセルインデックスは1から始まることに注意してください（これはJuliaです）！
