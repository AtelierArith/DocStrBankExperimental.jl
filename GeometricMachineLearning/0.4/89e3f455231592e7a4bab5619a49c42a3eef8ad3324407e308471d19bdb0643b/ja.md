```
LinearLayerQ(n)
```

次元 $n\times{}n$ の線形層を作成し、$q$ コンポーネントのみを変更します。

これは、行列による左乗算に相当します：

$$
\begin{pmatrix}
\mathbb{I} & A \\ 
\mathbb{O} & \mathbb{I}
\end{pmatrix}, 
$$

ここで、$A$ は [`SymmetricMatrix`](@ref) です。
