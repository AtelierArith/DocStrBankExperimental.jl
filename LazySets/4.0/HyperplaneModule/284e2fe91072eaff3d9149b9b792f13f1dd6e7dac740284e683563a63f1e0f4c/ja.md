```
constrained_dimensions(H::Hyperplane)
```

ハイパープレーンが制約されている次元を返します。

### 入力

  * `H` – ハイパープレーン

### 出力

ハイパープレーンが次元 `i` で制約されているような昇順のインデックス `i` のベクトル。

### 例

制約 $x_1 = 0$ を持つ2Dハイパープレーンは、次元1でのみ制約されています。
