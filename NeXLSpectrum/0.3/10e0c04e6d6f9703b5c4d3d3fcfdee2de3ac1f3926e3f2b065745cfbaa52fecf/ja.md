```
colorize(hss::HyperSpectrum, cxrs::AbstractVector{CharXRay}, normalize=:All)
```

最大3つの `CharXRay` からRGBカラー化された画像を作成します。これらは、カウント信号が統合されるチャネルを定義します。 `normalize=:All` は、`roiimages(...)` メソッドを使用して強度を共通のスケールに置きます。それ以外の場合、各画像は最も明るいピクセルに基づいて独立してスケーリングされます。
