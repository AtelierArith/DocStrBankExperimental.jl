```
controls(Z)
controls(Z, i::Integer)
controls(Z, inds)
```

軌道 `Z` のすべての制御ベクトルのリストを取得します。整数を渡すと、`i` 番目の制御のベクトルが抽出されます。整数のベクトルを渡すと、ベクトル内の各制御インデックスの時間履歴を含む `N` 次元ベクトルのリストが提供されます。
