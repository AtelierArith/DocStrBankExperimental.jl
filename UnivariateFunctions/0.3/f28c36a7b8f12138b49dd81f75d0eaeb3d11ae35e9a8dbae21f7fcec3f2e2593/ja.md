```
convert_to_linearly_rescale_inputs(f::UnivariateFunction, alpha::Real, beta::Real)
```

これは関数を変更し、xを入力すると、`alpha * x + beta`を入力したかのようにします。

### 入力

  * `f` - `UnivariateFunction`。
  * `alpha` - リスケーリングの傾き。
  * `beta` - リスケーリングのレベル。

### 返り値

  * 入力した関数のタイプの`UnivariateFunction`。
