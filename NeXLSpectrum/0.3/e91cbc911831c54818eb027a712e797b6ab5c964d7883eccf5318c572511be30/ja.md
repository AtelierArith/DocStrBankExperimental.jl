```
dose(hss::HyperSpectrum) # ピクセルあたりの平均線量
dose(hss::HyperSpectrum, idx...) # `idx` ピクセルの線量
```

プローブ電流とライブタイムの積をピクセル単位で返します。
