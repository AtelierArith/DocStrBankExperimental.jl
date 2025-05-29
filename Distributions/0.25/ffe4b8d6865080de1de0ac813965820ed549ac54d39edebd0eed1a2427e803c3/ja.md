```
AbstractMixtureModel <: Distribution
```

`AbstractMixtureModel`のすべてのサブタイプは、以下のメソッドを実装する必要があります：

  * `ncomponents(d)`: コンポーネントの数
  * `component(d, k)`: k 番目のコンポーネントを返す
  * `probs(d)`: コンポーネントに対する事前確率のベクトルを返す。
