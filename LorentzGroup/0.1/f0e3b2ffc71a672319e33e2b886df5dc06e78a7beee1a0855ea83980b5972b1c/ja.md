```
comoving(u; normalize=true)
```

$$
u
$$

のコモービングフレームへのブーストを[`LorMatrix`](@ref)として作成します。これは次のように与えられます。

$$
{\Lambda^\mu}_\nu=\left(\begin{array}{cc}
    {\delta^i}_j + \frac{u^i u_j}{u_4 + 1} & -u_j \\
    -u^i & u_4
\end{array}\right)
$$

`normalize=true`の場合、$u$は正規化されます。`normalize=false`の場合、チェックは行われないため、$u$が正規化されていない場合、結果は未定義になります。
