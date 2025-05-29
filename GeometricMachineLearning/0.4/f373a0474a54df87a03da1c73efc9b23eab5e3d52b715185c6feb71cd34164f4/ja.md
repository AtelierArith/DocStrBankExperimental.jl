```
ActivationLayerQ(n, σ)
```

サイズ `n` のアクティベーションレイヤーを作成し、アクティベーション `σ` は $q$ コンポーネントのみを変更します。

実行内容:

$$
\begin{pmatrix}
        q \\ p
\end{pmatrix} \mapsto 
\begin{pmatrix}
        q + \mathrm{diag}(a)\sigma(p) \\ p
\end{pmatrix}.
$$

これは、$M$ を `n`、$K$ を $\mathbb{I}$、$b$ をゼロに設定することで [`GradientLayerQ`](@ref) から回復できます。
