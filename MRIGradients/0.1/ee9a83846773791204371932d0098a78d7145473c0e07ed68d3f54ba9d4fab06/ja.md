```
gradients_to_nodes(gradients::Matrix; gamma=42577478, dwellTime=2e-6, FOV=[220,220,1],reconSize=[200,200,1])
```

適用された勾配トレインからk空間ノードを計算する関数

# 引数

  * `gradients::Matrix` - 定常的な滞留時間で取得された入力勾配。サイズ: (`2` x `N`) ここでNは勾配サンプルの数
  * `gamma` - ジロマグネティック比 [Hz]
  * `dwellTime` - 軌道の滞留時間 [s]
  * `FOV` - 空間的視野 [mm] [`1` x `3`]
  * `reconSize` - 再構成行列のサイズ [`1` x `3`]

# 出力

  * `nodes::Matrix` - 適用された勾配トレインに対応するk空間ノード。サイズ: (`2` x `N`) ここでNは勾配サンプルの数
