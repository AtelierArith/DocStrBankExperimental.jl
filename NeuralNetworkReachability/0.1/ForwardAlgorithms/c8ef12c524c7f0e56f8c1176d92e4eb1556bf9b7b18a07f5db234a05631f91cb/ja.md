```
SplitForward{S<:ForwardAlgorithm,FS,FM} <: ForwardAlgorithm
```

ニューラルネットワークの下で画像を計算し、ポリシーに従って結果のセットを再度マージする前に、セットを分割するフォワードアルゴリズム。

### フィールド

  * `algo` – 分割とマージの間に適用されるアルゴリズム
  * `split_function` – 分割のための関数
  * `merge_function` – マージのための関数
