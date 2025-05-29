```
NestedQuad(alg::IntegralAlgorithm)
NestedQuad(algs::IntegralAlgorithm...)
```

1つの数値積分アルゴリズムを繰り返すか、アルゴリズムのリストを組み合わせることによるネストされた積分。積分の範囲は、IteratedIntegration.jlパッケージの`AbstractIteratedLimits`でなければなりません。IteratedIntegration.jlの`nested_quad`に類似しています。被積分関数は`SVector`入力を期待する必要があります。非常に高次元の積分には使用しないでください。なぜなら、コンパイル時間が次元に対して非常に悪化するからです。コンパイル時間を改善するために、FunctionWrappers.jlが使用されており、被積分関数の型の安定性を強制しますので、常に推論が正しく機能するように最も広い積分限界の型を選択する必要があります。たとえば、ネストされたスキームで[`ContQuadGKJL`](@ref)がアルゴリズムとして使用される場合、積分の限界は複素数にする必要があります。
