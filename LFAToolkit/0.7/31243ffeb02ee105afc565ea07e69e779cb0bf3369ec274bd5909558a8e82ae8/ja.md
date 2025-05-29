```julia
computesymbols(jacobi, ω, θ)
```

ジャコビ前処理された演算子のシンボル行列を計算または取得します

# 引数:

  * `jacobi::Jacobi`:   シンボル行列を計算するためのジャコビ前処理器
  * `ω::Array{Real}`:   スムージング重み付け因子配列
  * `θ::Array{Real}`:   フーリエモード周波数配列（次元ごとに1つの周波数）

# 戻り値:

  * ジャコビ前処理された演算子のシンボル行列

# 例:

```jldoctest
using LinearAlgebra

for dimension = 1:3
    # セットアップ
    mesh = []
    if dimension == 1
        mesh = Mesh1D(1.0)
    elseif dimension == 2
        mesh = Mesh2D(1.0, 1.0)
    elseif dimension == 3
        mesh = Mesh3D(1.0, 1.0, 1.0)
    end
    diffusion = GalleryOperator("diffusion", 3, 3, mesh)

    # 前処理器
    jacobi = Jacobi(diffusion)

    # シンボルを計算
    A = computesymbols(jacobi, [1.0], π * ones(dimension))

    # 検証
    eigenvalues = real(eigvals(A))
    if dimension == 1
        @assert maximum(eigenvalues) ≈ 1 / 7
    elseif dimension == 2
        @assert minimum(eigenvalues) ≈ -1 / 14
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ -0.33928571428571486
    end
end

# 出力

```
