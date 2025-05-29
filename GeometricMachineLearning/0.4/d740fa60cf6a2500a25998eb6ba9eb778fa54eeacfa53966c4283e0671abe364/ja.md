```
StiefelLieAlgHorMatrix(A::SkewSymMatrix, B::AbstractMatrix, N::Integer, n::Integer)
```

スキュー対称行列 `A` と任意の行列 `B` に基づいて `StiefelLieAlgHorMatrix` のインスタンスを構築します。

`StiefelLieAlgMatrix` の要素は次の形を取ります:

$$
\begin{pmatrix}
A & B^T \\ B & \mathbb{O}
\end{pmatrix},
$$

ここで $A$ はスキュー対称です（これは [`SkewSymMatrix`](@ref) で `GeometricMachineLearning` にあります）。

また、[`GrassmannLieAlgHorMatrix`](@ref) も参照してください。

# 拡張ヘルプ

`StiefelLieAlgHorMatrix` は *スキュー対称行列のリー代数の水平成分* です（標準的なメトリックに関して）。

ここでの射影は次の通りです: $\pi:S \to SE$ であり、

$$
E = \begin{bmatrix} \mathbb{I}_{n} \\ \mathbb{O}_{(N-n)\times{}n}  \end{bmatrix}.
$$

行列 $E$ は `GeometricMachineLearning` の [`StiefelProjection`](@ref) の下で実装されています。 ```
