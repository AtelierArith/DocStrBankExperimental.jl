```
geodesic(B̄::StiefelLieAlgHorMatrix)
```

[`StiefelLieAlgHorMatrix`](@ref) の要素の測地線を計算します。

# 実装

内部的には、次のように使用されています：

$$
\mathbb{I} + B'\mathfrak{A}(B', B'')B'',
$$

ここで 

$$
\bar{B} = \begin{bmatrix}
    A & -B^T \\ 
    B & \mathbb{O}
\end{bmatrix} = \begin{bmatrix}  \frac{1}{2}A & \mathbb{I} \\ B & \mathbb{O} \end{bmatrix} \begin{bmatrix}  \mathbb{I} & \mathbb{O} \\ \frac{1}{2}A & -B^T  \end{bmatrix} =: B'(B'')^T.
$$

これは、行列指数関数 $\mathfrak{A}$ の計算効率の良いバージョンを使用しています。

[`GeometricMachineLearning.𝔄`](@ref) を参照してください。
