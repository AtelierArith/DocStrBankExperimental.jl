```
HelmholtzFMMOptions{I, C} <: FMMOptions
```

ヘルムホルツ初期化子のセットアップ関数。  

# フィールド

  * `p::I`: 多極展開の次数。
  * `ncrit::I`: ツリーの各ボックス内の最小ポイント数。
  * `wavek::C`: 波数。
