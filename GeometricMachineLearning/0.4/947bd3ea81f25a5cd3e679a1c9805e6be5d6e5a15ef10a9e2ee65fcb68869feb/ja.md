```
VectorSoftmax <: AbstractSoftmax
```

任意のベクトルを確率ベクトルに変換するには、次の式を使用します：

$$
[\mathrm{softmax}(a)]_i = \frac{e^{a_i}}{\sum_{i'=1}^de^{a_i}}. 
$$

これが「softmax」という名前の下で最もよく理解されているものです。[`MatrixSoftmax`](@ref)は行列バージョンです。
