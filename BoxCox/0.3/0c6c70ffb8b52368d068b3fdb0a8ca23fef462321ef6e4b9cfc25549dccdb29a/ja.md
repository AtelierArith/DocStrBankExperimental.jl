```
yeojohnson(λ; atol=0)
yeojohnson(λ, x; atol=0)
```

$$
\begin{cases} ((x_i+1)^\lambda-1)/\lambda                      &  \text{if }\lambda \neq 0, y \geq 0 \\
               \log(y_i + 1)                                     &  \text{if }\lambda =     0, y \geq 0 \\
               -((-x_i + 1)^{(2-\lambda)} - 1) / (2 - \lambda)  &  \text{if }\lambda \neq 2, y <     0 \\
               -\log(-x_i + 1)                                   &  \text{if }\lambda =     2, y <     0
\end{cases}
$$

`atol`は、λをゼロまたは2として扱うための絶対許容誤差を制御します。

1つの引数のバリアントは、与えられたλのために`x`の1引数関数をカリー化して作成します。

詳細は[`YeoJohnsonTransformation`](@ref)を参照してください。

# 参考文献

Yeo, I.-K., & Johnson, R. A. (2000). A new family of power transformations to improve normality or symmetry. Biometrika, 87(4), 954–959. https://doi.org/10.1093/biomet/87.4.954
