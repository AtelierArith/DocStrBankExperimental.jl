```
transform(c::AbstractHypercubeTransform, p)
```

座標 `p` を持つハイパーキューブから、変換 `c` によって定義されたパラメータ空間に変換します。

この関数の動作は `c` の性質によって異なります。

  * `c` が <: Distributions.Distributions であり、分位数メソッドを持っている場合

これは単に分位数関数を呼び出します。分位数関数が定義されていない場合は、`c` の型に依存したカスタム変換が呼び出されます。カスタム変換が存在しない場合は、エラーが発生します。

  * `c` が変換のタプルである場合、transform は

タプルを通じて [TransformVariables.jl](https://github.com/tpapp/TransformVariables.jl) メソッドに似た方法で反復処理を行います。
