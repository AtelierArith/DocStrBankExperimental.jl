```
displayednetworkat!(net::HybridNetwork, node::Node, nofuse=false,
                    unroot=false, multgammas=false)
```

入力ノードを除いて、すべての小さなハイブリッドエッジを削除します。ネットワークは単一のハイブリッド化を残し、それ以外は以前と同じ主要な木を表示します。`nofuse`がtrueの場合、エッジは融合されず（次数2のノードは保持されます）。

警告：正しい`ismajor`フィールドを仮定してください。
