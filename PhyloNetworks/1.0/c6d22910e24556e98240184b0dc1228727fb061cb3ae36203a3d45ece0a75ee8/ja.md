```
deletehybridthreshold!(net::HybridNetwork, threshold::Float64,
                       nofuse=false, unroot=false, multgammas=false,
                       keeporiginalroot=false)
```

ネットワークから、遺伝率が閾値γ未満のすべてのハイブリッドエッジを削除します。ネットワークを返します。

  * threshold<0.5の場合: γ < thresholdの小さなハイブリッドエッジを削除します（または、threshold > -1.0の場合はγが欠損しているもの）。
  * threshold=0.5の場合: すべての小さなハイブリッドエッジを削除します（すなわち、通常はγ < 0.5の場合、γが欠損していない場合）。
  * `nofuse`: trueの場合、エッジを融合せず、元のノードを保持します。
  * `unroot`: falseの場合、次数が2になってもルートは削除されません。
  * `multgammas`: trueの場合、修正されたエッジのγ値は、抽出されたサブネットワークが表す遺伝子の割合に等しくなります。修正されたネットワークのエッジ`e`に対する遺伝率γは、`e`に統合された元のネットワークのすべてのエッジのγの積です。

-`keeporiginalroot`: trueの場合、次数が1であってもルートは保持されます。

警告:

  * デフォルトでは、`nofuse`はfalseであり、パートナーのハイブリッドエッジはその子エッジと融合し、γは1.0に変更されます。`nofuse`がtrueの場合: パートナーのハイブリッドエッジのγは変更されません。
  * 正しい`ismajor`フィールドと、`containroot`を更新するための正しい`ischild1`フィールドを前提としています。
