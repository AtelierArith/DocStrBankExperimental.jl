```
roiimage(hss::HyperSpectrum, cxr::CharXRay)
```

指定された特性X線のカウントマップを作成します。デフォルトでは、`cxr`で1つのFWHMを統合します。もしhss[:Detector]が`EDSDetector`であれば、FWHMはそれから取得されます。そうでない場合、Mn KαでのFWHMは130 eVと仮定されます。
