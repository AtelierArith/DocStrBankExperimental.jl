```
zphi2pixRing(resol::Resolution, theta, phi) -> Integer
```

与えられた座標（`theta`、コラティチュード、`phi`、経度）の点を含むピクセルのインデックスを返します。これは、リング順にピクセルが配置されたHealpixマップ用です。ピクセルインデックスは1ベースであることに注意してください（これはJuliaです）！
