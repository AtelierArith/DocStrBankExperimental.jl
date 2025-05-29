```
LinearLayerP(n)
```

次元 $n\times{}n$ の線形層を作成し、$p$ コンポーネントのみを変更します。

これは、行列による左乗算に相当します：

$$
\begin{pmatrix}
\mathbb{I} & \mathbb{O} \\ 
A & \mathbb{I}
\end{pmatrix}, 
$$

ここで、$A$ は [`SymmetricMatrix`](@ref) です。
