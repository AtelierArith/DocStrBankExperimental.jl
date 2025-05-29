```
ActivationLayerP(n, σ)
```

サイズ `n` のアクティベーションレイヤーを作成し、アクティベーション `σ` は $p$ コンポーネントのみを変更します。

実行される操作:

$$
\begin{pmatrix}
        q \\ p
\end{pmatrix} \mapsto 
\begin{pmatrix}
        q \\ p + \mathrm{diag}(a)\sigma(q)
\end{pmatrix}.
$$

これは、$M$ を `n`、$K$ を $\mathbb{I}$、$b$ をゼロに設定することで [`GradientLayerP`](@ref) から回復できます。
