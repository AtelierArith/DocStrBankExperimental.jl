```
normalization(A::AbstractTensorTrain)
```

正規化 $Z=\sum_{x^1,\ldots,x^L} A^1(x^1)\cdots A^L(x^L)$ を計算し、符号と絶対値の対数を格納する `Logarithmic` として返します（LogarithmicNumbers.jl のドキュメントを参照してください https://github.com/cjdoris/LogarithmicNumbers.jl?tab=readme-ov-file#documentation）
