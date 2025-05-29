```
    intersection(X::CartesianProductArray, Y::CartesianProductArray)
```

有限数の集合の直交積の間の交差を計算します。

### 入力

  * `X` – 有限数の集合の直交積
  * `Y` – 有限数の集合の直交積

### 出力

`X` と `Y` の具体的な交差を表す分解された集合。

### アルゴリズム

このアルゴリズムは、集合の対応するブロックを交差させます。
