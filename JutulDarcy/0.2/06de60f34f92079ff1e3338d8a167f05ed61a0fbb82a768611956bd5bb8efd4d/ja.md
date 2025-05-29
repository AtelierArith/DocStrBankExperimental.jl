```
標準ブラックオイルシステム(; rs_max = nothing,
                         rv_max = nothing,
                         phases = (AqueousPhase(), LiquidPhase(), VaporPhase()),
                         reference_densities = [786.507, 1037.84, 0.969758])
```

標準ブラックオイルシステムを設定します。キーワード引数 `rs_max` と `rv_max` は、何も指定しないか、圧力の関数としての最大 Rs および Rv のための呼び出し可能なオブジェクト / 関数である必要があります。`phases` は、各相の `reference_densities` と一緒に指定できます。

注意: ブラックオイルモデルでは、参照密度が PVT 挙動の多くの側面に大きな影響を与えます。これらは一般的に他の特性と一貫して設定する必要があります。
