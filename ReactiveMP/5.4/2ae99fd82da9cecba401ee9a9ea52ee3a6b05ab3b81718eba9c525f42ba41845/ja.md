FlowModel構造体は、レイヤーが特定のタイプに制約されない最も一般的なタイプのFlowモデルです。FlowModel構造体は、入力の次元とレイヤーのタプルを含み、`FlowModel( dim, (layer1, layer2, ...) )`として構築できます。

注意: このモデルは、レイヤーのタイプを制約することで特化できます。これにより、三角形ヤコビ行列など、これらのレイヤーの特性に対処できるより効率的な特化メソッドが可能になります。
