```
MultipleShooting()
```

直接的なマルチプルシューティング [`TranscriptionMethod`](@ref) を構築します。

決定変数は（$ϵ$を除く）：

$$
\mathbf{Z} = \begin{bmatrix} \mathbf{ΔU} \\ \mathbf{X̂_0} \end{bmatrix}
$$

したがって、これは運用点 $\mathbf{x̂_{op}}$ からの偏差ベクトルとして表現される予測状態も含みます（[`augment_model`](@ref）を参照）：

$$
\mathbf{X̂_0} = \mathbf{X̂ - X̂_{op}} =            \begin{bmatrix} 
    \mathbf{x̂}_i(k+1)     - \mathbf{x̂_{op}}     \\ 
    \mathbf{x̂}_i(k+2)     - \mathbf{x̂_{op}}     \\ 
    \vdots                                      \\ 
    \mathbf{x̂}_i(k+H_p)   - \mathbf{x̂_{op}}     \end{bmatrix}
$$

ここで、$\mathbf{x̂}_i(k+j)$ は時間 $k+j$ の状態予測であり、`direct` フラグに応じて時間 $i=k$ または $i=k-1$ でオブザーバーによって推定されます。運用点がゼロの場合、$\mathbf{X̂_0 = X̂}$ となることに注意してください。これは、通常 [`NonLinModel`](@ref) において実際に当てはまります。このトランスクリプション手法は、一般的に大きな制御ホライズン $H_c$、不安定または非常に非線形なプラントモデル/制約に対してより効率的です。

このトランスクリプション手法には、`OSQP` や `Ipopt` のようなスパースオプティマイザおよびスパースヤコビアン計算が推奨されます。
