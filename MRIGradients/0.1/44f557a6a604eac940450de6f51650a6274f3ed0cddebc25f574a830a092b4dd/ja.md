```
nodes_to_gradients(nodes::Matrix; gamma=42577478, dwellTime=2e-6, FOV=[220,220,1],reconSize=[200,200,1])
```

k空間データを取得するために使用される勾配列を計算する関数

# 引数

  * `nodes::Matrix` - 順番に移動した入力k空間ノード、一定の滞留時間で取得。サイズ: (`2` x `N`) ここでNはノードの数
  * `gamma` - ジロマグネティック比 [Hz]
  * `dwellTime` - 軌道の滞留時間 [s]
  * `FOV` - 空間的視野 [mm] [`1` x `3`]
  * `reconSize` - 再構成行列のサイズ [`1` x `3`]

# 出力

  * `gradients::Matrix` - k空間サンプルに対応する勾配。サイズ: (`2` x `N`) ここでNはk空間サンプルの数
