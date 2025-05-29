```
makeFourierGrid!(tsg::TasmanianSG; type, anisotropic_weights=Vector{Int32}(undef, 0), level_limits=Vector{Int32}(undef, 0))
```

は、既存のグリッドを破棄して、このクラスによって保持される新しいスパースグリッドを作成します。

type: テンソル選択戦略を識別する文字列       'level'     'curved'     'hyperbolic'     'tensor'       'iptotal'   'ipcurved'   'iphyperbolic'   'iptensor'       'qptotal'   'qpcurved'   'qphyperbolic'   'qptensor'

anisotropic_weights: 重みのリストまたは配列                      長さはiDimensionまたは2*iDimensionでなければならない                      最初のtsg.dimensionsの重みは正でなければならない                      詳細についてはマニュアルを参照してください。
