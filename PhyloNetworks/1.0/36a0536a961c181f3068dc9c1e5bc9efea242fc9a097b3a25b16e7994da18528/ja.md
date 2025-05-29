```
minortreeat(net::HybridNetwork, hybindex::Integer, nofuse=false, unroot::Bool=false)
```

ネットワークに表示されているツリーを抽出し、各ハイブリッドノードで主要なハイブリッドエッジに従いますが、i番目のハイブリッドノード（i=`hybindex`）では、主要なハイブリッドエッジの代わりにマイナーなハイブリッドエッジを保持します。`nofuse`がtrueの場合、エッジは融合されず（次数2のノードは保持されます）、`unroot`がtrueの場合、次数が2になるとルートが削除されます。

警告：正しい`ismajor`フィールドを仮定してください。
