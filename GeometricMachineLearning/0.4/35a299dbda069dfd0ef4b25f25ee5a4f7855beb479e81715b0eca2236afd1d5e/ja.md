```
GrassmannLieAlgHorMatrix(D::AbstractMatrix, n::Integer)
```

大きな行列を入力として受け取り、`GrassmannLieAlgHorMatrix`のインスタンスを構築します。

ここでの整数 $N$ は `D` の行数です。

# 拡張ヘルプ

コンストラクタが大きな $N\times{}N$ 行列で呼び出されると、次のように射影が行われます：

$$
\begin{pmatrix}
A & B_1  \\
B_2 & D
\end{pmatrix} \mapsto 
\begin{pmatrix}
\bar{\mathbb{O}} & -B_2^T \\ 
B_2 & \mathbb{O}
\end{pmatrix}.
$$

これは次の操作としても見ることができます：

$$
D \mapsto \Omega(E, DE - EE^TDE),
$$

ここで $\Omega$ は水平リフト [`GeometricMachineLearning.Ω`](@ref) です。
