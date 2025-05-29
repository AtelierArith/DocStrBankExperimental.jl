```
makeSequenceGrid!(tsg::TasmanianSG; type, rule, anisotropic_weights=Vector{Int32}(undef, 0), level_limits=Vector{Int32}(undef, 0))
```

は、シーケンスルールを使用して新しいスパースグリッドを作成し、このクラスが保持する既存のグリッドを破棄します。

type: テンソル選択戦略を識別する文字列       'level'     'curved'     'hyperbolic'     'tensor'       'iptotal'   'ipcurved'   'iphyperbolic'   'iptensor'       'qptotal'   'qpcurved'   'qphyperbolic'   'qptensor'

rule: グリッドを誘導する1次元ルールを定義する文字列       'leja'       'rleja'      'rleja-shifted'       'max-lebesgue'   'min-lebesgue'   'min-delta'

anisotropic_weights: 重みのリストまたは配列                      長さは `tsg.dimensions` または `2*tsg.dimensions` でなければならない                      最初の `tsg.dimensions` の重みは正でなければならない                      詳細はマニュアルを参照してください。
