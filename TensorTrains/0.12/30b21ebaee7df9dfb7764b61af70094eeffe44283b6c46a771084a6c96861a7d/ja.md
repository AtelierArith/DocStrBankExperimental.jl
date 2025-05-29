```
LinearAlgebra.normalize!(A::AbstractTensorTrain)
```

$$
Z=\sum_{x^1,\ldots,x^L} A^1(x^1)\cdots A^L(x^L)
$$

の正規化を計算します（[`normalization`](@ref）を参照）し、`A` のテンソルを再スケールして、この呼び出しの後に $|Z|=1$ となるようにします。絶対正規化の自然対数 $\log|Z|$ を返します。
