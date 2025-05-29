```
htensor(tree,trten,fmat)
htensor(tree,trten,U1,U2,...)
```

階層的タッカーテンソル。

## 引数:

  * `tree::dimtree`: 次元ツリー。
  * `trten::TensorCell`: 転送テンソル。ツリーの各内部ノードに対して1つ。
  * `fmat::MatrixCell`: フレーム行列。ツリーの各葉に対して1つ。

htensor X に対して、X.isorth=true はフレーム行列が直交正規である場合です。
