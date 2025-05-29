```
SingleShooting()
```

直接的な単一射撃 [`TranscriptionMethod`](@ref) を構築します。

最適化問題における決定変数は（スラック $ϵ$ を除く）：

$$
\mathbf{Z} = \mathbf{ΔU} =          \begin{bmatrix} 
    \mathbf{Δu}(k+0)                \\ 
    \mathbf{Δu}(k+1)                \\ 
    \vdots                          \\ 
    \mathbf{Δu}(k+H_c-1)            \end{bmatrix}
$$

この手法は一般的に、制御ホライズン $H_c$ が小さく、安定した軽度非線形のプラントモデル/制約に対してより効率的です。
