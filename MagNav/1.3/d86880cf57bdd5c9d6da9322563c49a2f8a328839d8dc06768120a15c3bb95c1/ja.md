```
get_optimal_rotation_matrix(v1s, v2s)
```

v1sの方向をv2sに回転させる`3` x `3`回転行列を取得します。Kabschアルゴリズムを使用します。

参考: https://en.wikipedia.org/wiki/Kabsch_algorithm

**引数:**

  * `v1s`: 最初の3Dポイントのセットのための`N` x `3`行列
  * `v2s`: 2番目の3Dポイントのセットのための`N` x `3`行列

**戻り値:**

  * `R`: v1sをv2sの方向に回転させる3D行列
