```
propagateforward(rbm, datadict, factor)
```

指定された `datadict` と同じラベルを含む新しい `DataDict` を返しますが、マッピングされた値として元のデータセットの `rbm` における隠れたポテンシャルが含まれています。ファクターは隠れたポテンシャルを計算するために適用され、デフォルトは 1.0 です。
