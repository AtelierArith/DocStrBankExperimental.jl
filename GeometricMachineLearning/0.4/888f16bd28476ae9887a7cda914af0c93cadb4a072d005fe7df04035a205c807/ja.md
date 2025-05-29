```
StiefelLieAlgHorMatrix(D::AbstractMatrix, n::Integer)
```

大きな行列を入力として受け取り、`StiefelLieAlgHorMatrix`のインスタンスを構築します。

$$
St(n, N)
$$

の整数$N$は、`D`の行数です。

# 拡張ヘルプ

コンストラクタが大きな$N\times{}N$行列で呼び出されると、次のように射影が行われます：

$$
\begin{pmatrix}
A & B_1  \\
B_2 & D
\end{pmatrix} \mapsto 
\begin{pmatrix}
\mathrm{skew}(A) & -B_2^T \\ 
B_2 & \mathbb{O}
\end{pmatrix}.
$$

操作$\mathrm{skew}:\mathbb{R}^{n\times{}n}\to\mathcal{S}_\mathrm{skew}(n)$は、スキュー対称化操作です。これは、$n\times{}n$行列に対して[`SkewSymMatrix`](@ref)を呼び出すことと同等です。

これは次の操作としても見ることができます：

$$
D \mapsto \Omega(E, DE) = \mathrm{skew}\left(2 \left(\mathbb{I} - \frac{1}{2} E E^T \right) DE E^T\right).
$$

また、[`GeometricMachineLearning.Ω`](@ref)も参照してください。 ```
