```
trainrbm!(rbm, x)
```

与えられた `rbm` をデータセット `x` を使用して1エポック訓練します。（関数 `fitrbm` も参照してください。）

# オプションのキーワード引数:

  * `learningrate`, `cdsteps`, `sdlearningrate`, `upfactor`, `downfactor`,  `optimizer`:  関数 `fitrbm` のドキュメントを参照してください。
  * `chainstate`: RBMの隠れノードの状態を保持するための行列です。指定されている場合、PCDが使用されます。
