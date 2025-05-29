```
simpleflux(Ca::Float,Co::Float,pisvel::Float)
```

海洋に入るフラックスを単位面積あたりで計算します

```
mld=10 #混合層の深さ (m)
tim=86400*30 #緩和時間スケール (s)
pisvel=mld/tim #ピストン速度 (m/s)
Co=0.0 #海洋の値 (例: ある化合物の濃度)
Ca=1.0 #大気の値 (例: 同等の化合物濃度)

simpleflux(Ca,Co,pisvel)
```
