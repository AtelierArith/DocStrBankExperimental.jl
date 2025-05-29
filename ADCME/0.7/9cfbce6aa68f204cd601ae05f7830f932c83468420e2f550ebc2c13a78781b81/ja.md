```
αscheme(M::Union{SparseTensor, SparseMatrixCSC}, 
    C::Union{SparseTensor, SparseMatrixCSC}, 
    K::Union{SparseTensor, SparseMatrixCSC}, 
    Force::Union{Array{Float64}, PyObject}, 
    d0::Union{Array{Float64, 1}, PyObject}, 
    v0::Union{Array{Float64, 1}, PyObject}, 
    a0::Union{Array{Float64, 1}, PyObject}, 
    Δt::Array{Float64}; 
    solve::Union{Missing, Function} = missing,
    extsolve::Union{Missing, Function} = missing, 
    ρ::Float64 = 1.0)
```

一般化されたαスキーム。 $M u_{tt} + C u_{t} + K u = F$

`Force` はサイズ `n`×`p` の配列でなければならず、`d0`、`v0`、および `a0` はサイズ `p` であり、`Δt` は配列（可変時間ステップ）です。

一般化されたαスキームは、時間ステッピングによって方程式を解きます。

$$
\begin{aligned}
\bf d_{n+1} &= \bf d_n + h\bf v_n + h^2 \left(\left(\frac{1}{2}-\beta_2 \right)\bf a_n + \beta_2 \bf a_{n+1}  \right)\\
\bf v_{n+1} &= \bf v_n + h((1-\gamma_2)\bf a_n + \gamma_2 \bf a_{n+1})\\
\bf F(t_{n+1-\alpha_{f_2}}) &= M \bf a _{n+1-\alpha_{m_2}} + C \bf v_{n+1-\alpha_{f_2}} + K \bf{d}_{n+1-\alpha_{f_2}}
\end{aligned}
$$

ここで 

$$
\begin{aligned}
\bf d_{n+1-\alpha_{f_2}} &= (1-\alpha_{f_2})\bf d_{n+1} + \alpha_{f_2} \bf d_n\\
\bf v_{n+1-\alpha_{f_2}} &= (1-\alpha_{f_2}) \bf v_{n+1} + \alpha_{f_2} \bf v_n \\
\bf a_{n+1-\alpha_{m_2} } &= (1-\alpha_{m_2}) \bf a_{n+1} + \alpha_{m_2} \bf a_n\\
t_{n+1-\alpha_{f_2}} & = (1-\alpha_{f_2}) t_{n+1 + \alpha_{f_2}} + \alpha_{f_2}t_n
\end{aligned}
$$

ここで、パラメータは次のように計算されます。

$$
\begin{aligned}
\gamma_2 &= \frac{1}{2} - \alpha_{m_2} + \alpha_{f_2}\\
\beta_2 &= \frac{1}{4} (1-\alpha_{m_2}+\alpha_{f_2})^2 \\
\alpha_{m_2} &= \frac{2\rho_\infty-1}{\rho_\infty+1}\\
\alpha_{f_2} &= \frac{\rho_\infty}{\rho_\infty+1}
\end{aligned}
$$

∘ `solve`: ユーザーは `Ax = rhs` を解くためのソルバ関数 `solve(A, rhs)` を提供できます。 ∘ `extsolve`: `solve` と似ていますが、シグネチャは次の形式になります。

```julia
extsolve(A, rhs, i)
```

これにより、ユーザーは（時間依存の）ディリクレ境界条件など、より多くの制御を得ることができます。詳細については、[一般化されたαスキーム](https://kailaix.github.io/ADCME.jl/dev/alphascheme/)を参照してください。

!!! note
    $$
    u
    $$

    が非ゼロの本質的境界条件 $u_b$ を持つ場合、$\tilde u=u-u_b$ とし、次のようにします。 $M \tilde u_{tt} + C \tilde u_t + K u = F - K u_b - C \dot u_b$


```
