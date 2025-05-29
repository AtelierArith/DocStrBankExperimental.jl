学習率の範囲（0から1）にわたる累積コストの比較を、3つの方法（Wright、Crawford、Experience）で生成します。

```
learn_rates(InitialEffort, Units; LC_Step=0.1)
```

次の列を持つDataFrameを返します：

  * `LC`: 学習率。
  * `Wright`: Wrightのモデルからの累積コスト。
  * `Crawford`: Crawfordのモデルからの累積コスト。
  * `Experience`: 経験モデルからの累積コスト。
