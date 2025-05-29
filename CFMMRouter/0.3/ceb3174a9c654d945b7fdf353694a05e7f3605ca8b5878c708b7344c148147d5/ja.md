```
find_arb!(Δ, Λ, cfmm, v)
```

`cfmm`のためのアービトラージ問題を価格ベクトル`v`に対して解決します。

$$
\begin{array}{ll}
\text{minimize} & \nu^T(\Lambda - \Delta) \\
\text{subject to} & \varphi(R + \gamma\Delta - \Lambda) = \varphi(R) \\
& \Delta, \Lambda \geq 0.
\end{array}
$$

変数`Δ`と`Λ`を上書きします。
