```
AmplMPECModel
```

補完制約を持つAmplモデルの滑らかな再定式化。

非線形プログラム

$$
\begin{aligned}
       min_x  \quad &  f(x)\\
\mathrm{s.t.} \quad &  c_L ≤ c(x) ≤ c_U,\\
                    &  g_L ≤ g(x) ⟂ x ≥ x_L,
\end{aligned}
$$

は次のように再定式化されます。

$$
\begin{aligned}
       min_x  \quad &  f(x)\\
\mathrm{s.t.} \quad &  c_L ≤ c(x) ≤ c_U,\\
                    &  g_L ≤ g(x)  \\
                    &  x_L ≤ x \\
                    &  Diag(g(x)) x ≤ 0
\end{aligned}
$$

補完制約がない場合は元のモデルを返します。
