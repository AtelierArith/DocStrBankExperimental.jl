```
primitivize(flat::AbstractFourierLattice, cntr::Char) --> ::typeof(flat)
```

与えられた `flat` は中心 `cntr` を持つ従来の基底を指し、関連する原始基底に言及する導出された（しかし物理的に同等の）格子 `flat′` を計算します。

具体的には、`flat` が直接的な従来の基底 `Rs` $≡ (\mathbf{a} \mathbf{b} \mathbf{c})$ [座標ベクトル $\mathbf{r} ≡ (r_1, r_2, r_3)^{\mathrm{T}}$] を指す場合、`flat′` は直接的な原始基底 `Rs′` $≡ (\mathbf{a}' \mathbf{b}' \mathbf{c}') ≡ (\mathbf{a} \mathbf{b} \mathbf{c})\mathbf{P}$ [座標ベクトル  $\mathbf{r}' ≡ (r_1', r_2', r_3')^{\mathrm{T}} = \mathbf{P}^{-1}\mathbf{r}$] を指します。ここで、$\mathbf{P}$ は `primitivebasismatrix(...)` から得られる基底変換行列を示します。

関連する原始基底ベクトルを計算するには、[`primitivize(::DirectBasis, ::Char)`](@ref) を参照してください [具体的には、`Rs′ = primitivize(Rs, cntr)`]。

## 例

2Dの平面群5からの中心付き（'c'）格子を、従来の基底と原始基底でプロットします（`using PyPlot` が必要です）：

```julia-repl
julia> sgnum = 5; D = 2; cntr = centering(sgnum, D)  # 'c'（体心）

julia> Rs   = directbasis(sgnum, Val(D))     # 従来の基底（長方形）
julia> flat = levelsetlattice(sgnum, Val(D)) # Rsの基底におけるフーリエ格子
julia> flat = modulate(flat)                 # 格子係数を変調する
julia> plot(flat, Rs)

julia> Rs′   = primitivize(Rs, cntr)    # 原始基底（斜め）
julia> flat′ = primitivize(flat, cntr)  # Rs′の基底におけるフーリエ格子

julia> using PyPlot
julia> plot(flat′, Rs′)
```
