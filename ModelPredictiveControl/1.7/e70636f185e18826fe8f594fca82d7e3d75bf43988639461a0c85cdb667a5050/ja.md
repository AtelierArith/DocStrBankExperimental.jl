```
setop!(model; uop=nothing, yop=nothing, dop=nothing, xop=nothing, fop=nothing) -> model
```

`model`の動作点を設定します（[`LinModel`](@ref)および[`NonLinModel`](@ref)の両方）。

操作された入力`uop`、モデル出力`yop`、測定された外乱`dop`、およびモデル状態`xop`の動作点（いわゆる名目値）周辺の偏差ベクトルを導入します：

$$
\begin{align*}
    \mathbf{u_0}(k) &= \mathbf{u}(k) - \mathbf{u_{op}} \\
    \mathbf{d_0}(k) &= \mathbf{d}(k) - \mathbf{d_{op}} \\
    \mathbf{y_0}(k) &= \mathbf{y}(k) - \mathbf{y_{op}} \\
    \mathbf{x_0}(k) &= \mathbf{x}(k) - \mathbf{x_{op}} \\
\end{align*}
$$

動作点周辺の[`LinModel`](@ref)の状態空間記述は次のとおりです：

$$
\begin{aligned}
    \mathbf{x_0}(k+1) &= \mathbf{A x_0}(k) + \mathbf{B_u u_0}(k) + \mathbf{B_d d_0}(k) 
                         + \mathbf{f_{op}}   - \mathbf{x_{op}}                                              \\
    \mathbf{y_0}(k)   &= \mathbf{C x_0}(k) + \mathbf{D_d d_0}(k) 
\end{aligned}
$$

そして、[`NonLinModel`](@ref)の場合：

$$
\begin{aligned}
    \mathbf{x_0}(k+1) &= \mathbf{f}\Big(\mathbf{x_0}(k), \mathbf{u_0}(k), \mathbf{d_0}(k), \mathbf{p}\Big) 
                            + \mathbf{f_{op}} - \mathbf{x_{op}}                                             \\
    \mathbf{y_0}(k)   &= \mathbf{h}\Big(\mathbf{x_0}(k), \mathbf{d_0}(k), \mathbf{p}\Big)
\end{aligned}
$$

状態`xop`および追加の`fop`動作点は、例えば`model`がシステム同定から来るときに頻繁にゼロです。これらの2つのベクトルは、非平衡点のために[`linearize`](@ref)によって内部的に使用されます。

# 例

```jldoctest
julia> model = setop!(LinModel(tf(3, [10, 1]), 2.0), uop=[50], yop=[20])
LinModel with a sample time Ts = 2.0 s and:
 1 manipulated inputs u
 1 states x
 1 outputs y
 0 measured disturbances d

julia> y = model()
1-element Vector{Float64}:
 20.0
```
