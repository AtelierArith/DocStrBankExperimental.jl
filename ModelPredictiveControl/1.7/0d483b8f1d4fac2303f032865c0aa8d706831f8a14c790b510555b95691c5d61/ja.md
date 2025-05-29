```
linearize(model::SimModel; x=model.x0+model.xop, u=model.uop, d=model.dop) -> linmodel
```

モデル `model` を動作点 `x`、`u`、`d` で線形化し、[`LinModel`](@ref) を返します。

引数 `x`、`u`、`d` は、それぞれ状態 $\mathbf{x}$、操作された入力 $\mathbf{u}$、および測定された外乱 $\mathbf{d}$ の線形化点です（必ずしも平衡点ではなく、詳細は拡張ヘルプを参照）。デフォルトでは、[`ForwardDiff`](@extref ForwardDiff) が自動的に $\mathbf{f}$ および $\mathbf{h}$ 関数のヤコビアンを計算します。バックエンドを切り替えるには、`model` の構築時に `jacobian` キーワード引数を変更してください。

!!! warning
    次のようなエラーが発生した場合は、拡張ヘルプを参照してください: `MethodError: no method matching (::var"##")(::Vector{ForwardDiff.Dual})`。


# 例

```jldoctest
julia> model = NonLinModel((x,u,_,_)->x.^3 + u, (x,_,_)->x, 0.1, 1, 1, 1, solver=nothing);

julia> linmodel = linearize(model, x=[10.0], u=[0.0]); 

julia> linmodel.A
1×1 Matrix{Float64}:
 300.0
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    非線形状態空間モデルにおいて:

    $$
    \begin{aligned}
        \mathbf{x}(k+1) &= \mathbf{f}\Big(\mathbf{x}(k), \mathbf{u}(k), \mathbf{d}(k), \mathbf{p}\Big)  \\
        \mathbf{y}(k)   &= \mathbf{h}\Big(\mathbf{x}(k), \mathbf{d}(k), \mathbf{p}\Big)
    \end{aligned}
    $$

    動作点 $\mathbf{x_{op}, u_{op}, d_{op}}$ での線形化は次のようになります:

    $$
    \begin{aligned}
        \mathbf{x_0}(k+1) &≈ \mathbf{A x_0}(k) + \mathbf{B_u u_0}(k) + \mathbf{B_d d_0}(k)  
                            + \mathbf{f(x_{op}, u_{op}, d_{op}, p)} - \mathbf{x_{op}}         \\
        \mathbf{y_0}(k)   &≈ \mathbf{C x_0}(k) + \mathbf{D_d d_0}(k) 
    \end{aligned}
    $$

    これは、[`setop!`](@ref) ドキュメントで導入された偏差ベクトル $\mathbf{x_0, u_0, d_0, y_0}$ に基づいており、ヤコビアン行列は次のようになります:

    $$
    \begin{aligned}
        \mathbf{A}   &= \left. \frac{∂\mathbf{f(x, u, d, p)}}{∂\mathbf{x}} \right|_{\mathbf{x=x_{op},\, u=u_{op},\, d=d_{op}}} \\
        \mathbf{B_u} &= \left. \frac{∂\mathbf{f(x, u, d, p)}}{∂\mathbf{u}} \right|_{\mathbf{x=x_{op},\, u=u_{op},\, d=d_{op}}} \\
        \mathbf{B_d} &= \left. \frac{∂\mathbf{f(x, u, d, p)}}{∂\mathbf{d}} \right|_{\mathbf{x=x_{op},\, u=u_{op},\, d=d_{op}}} \\
        \mathbf{C}   &= \left. \frac{∂\mathbf{h(x, d, p)}}{∂\mathbf{x}}    \right|_{\mathbf{x=x_{op},\, d=d_{op}}}             \\
        \mathbf{D_d} &= \left. \frac{∂\mathbf{h(x, d, p)}}{∂\mathbf{d}}    \right|_{\mathbf{x=x_{op},\, d=d_{op}}}
    \end{aligned}
    $$

    [`setop!`](@ref) の表記法に従うと、次のようになります:

    $$
    \begin{aligned}
        \mathbf{f_{op}} &= \mathbf{f(x_{op}, u_{op}, d_{op}, p)} \\
        \mathbf{y_{op}} &= \mathbf{h(x_{op}, d_{op}, p)}
    \end{aligned}
    $$

    点が平衡点である場合、$\mathbf{f_{op} - x_{op} = 0}$ であることに注意してください。非線形モデルがゼロでない動作点を持つ場合、方程式は類似しています。

    自動微分 (AD) により、正確なヤコビアンが可能になります。ただし、[`NonLinModel`](@ref) の `f` および `h` 関数はこの機能と互換性がある必要があります。これらの関数を書く際の一般的な間違いについては、[`JuMP` ドキュメント](@extref JuMP Common-mistakes-when-writing-a-user-defined-operator) を参照してください。


```
