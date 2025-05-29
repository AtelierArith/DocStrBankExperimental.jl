```
`inverse(c::AbstractHypercubeTransform, p)`
```

パラメータ空間 `p` から、変換 `c` によって定義された単位ハイパーキューブに変換します。

この関数の動作は `c` の性質によって異なります。

  * `c` が <: Distributions.Distributions であり、cdf メソッドを持つ場合

これは単に cdf 関数を呼び出します。cdf 関数が定義されていない場合は、`c` の型に依存するカスタム変換が呼び出されます。カスタム変換が存在しない場合は、エラーが発生します。

  * `c` が変換のタプルである場合、inverse は

[TransformVariables.jl](https://github.com/tpapp/TransformVariables.jl) メソッドに似た方法でタプルを反復処理します。
