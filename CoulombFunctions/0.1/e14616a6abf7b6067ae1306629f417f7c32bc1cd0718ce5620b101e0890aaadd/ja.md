```
bessels!(j, j′, y, y′, x)
```

球面ベッセル関数（正規: $j_n$）とノイマン関数（不正規: $y_n$）およびそれらの導関数を `x` で計算し、結果をベクトル `j`、`j′`、`y`、`y′` に格納します。ベッセル関数またはノイマン関数のいずれかのみが興味の対象である場合、もう一方の配列は `nothing` に置き換えることができます。ただし、関数のみを計算し、導関数を計算しないことはできません。なぜなら、導関数は次の再帰関係を使用して生成されるからです：

$$
\begin{aligned}
g_{n-1} &= \frac{n+1}{x} g_n + g_n'\\
g'_{n-1} &= \frac{n-1}{x} g_{n-1} - g_n.
\end{aligned}
$$

これらの再帰関係は、ベッセル関数に対しては*下方*に、ノイマン関数に対しては*上方*に使用されます。

すべての渡された配列が同じ長さであると仮定されています（チェックは行われません）。
