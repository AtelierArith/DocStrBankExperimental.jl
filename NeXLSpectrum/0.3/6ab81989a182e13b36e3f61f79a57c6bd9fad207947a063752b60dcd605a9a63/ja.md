```
roiimages(hss::HyperSpectrum, cxrs::AbstractVector{CharXRay})
```

`cxrs`の各CharXRayラインの強度を表すグレイ画像の配列を作成します。これらは、いずれかの画像の最も強いピクセルが白を定義するように正規化されています。デフォルトでは、`cxr`で1つのFWHMを統合します。もしhss[:Detector]が`EDSDetector`であれば、FWHMはそれから取得されます。それ以外の場合、Mn Kαで130 eVのFWHMが仮定されます。
