```
displayedtrees(net::HybridNetwork, gamma::Float64; nofuse::Bool=false,
               unroot::Bool=false, multgammas::Bool=false,
               keeporiginalroot::Bool=false)
```

ネットワークに表示されるすべてのツリーを抽出し、遺伝率がγの閾値以上（または閾値が0.5の場合は>0.5）のハイブリッドエッジに従い、γ未満の遺伝率を持つハイブリッドエッジは無視します。HybridNetworkオブジェクトとしてのツリーの配列を返します。

`nofuse`: trueの場合、ハイブリッドエッジの削除中にエッジを融合せず（次数2のノードを保持）、   `unroot`: falseの場合、元の根が次数2になると削除されませんが、   keeporiginalrootがtrueの場合を除きます。   `multgammas`: trueの場合、表示されたツリーのエッジは、すべてのこれらのエッジがツリーエッジであるにもかかわらず、エッジが表す遺伝子の割合に等しいγ値を持ちます。すべてのエッジにわたるγ値の積は、ツリーが表す遺伝子の割合です。具体的には、特定の表示されたツリーのエッジ`e`は、`e`に統合された元のネットワークのすべてのエッジのγの積に等しいγを持ちます。   `keeporiginalroot`: trueの場合、次数1であっても根を保持します。

警告:

  * `nofuse`がtrueの場合: 残されたパートナーのハイブリッドエッジはそのγ値が変更されず、`ismajor`はtrueに変更されます
  * 正しい`ismajor`属性を仮定します。
