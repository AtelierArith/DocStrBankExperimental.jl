```julia
computesymbols(chebyshev, ω, θ)
```

チェビシェフ前処理オペレーターのシンボル行列を計算または取得します

# 引数:

  * `chebyshev::Chebyshev`:  シンボル行列を計算するためのチェビシェフ前処理器
  * `ω::Array{Real}`:        スムージングパラメータ配列 [次数], [次数, $\lambda_{\text{max}}$], または [次数, $\lambda_{\text{min}}$, $\lambda_{\text{max}}$]
  * `θ::Array{Real}`:        フーリエモード周波数配列（次元ごとに1つの周波数）

# 戻り値:

  * チェビシェフ前処理オペレーターのシンボル行列

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
    chebyshev = Chebyshev(diffusion)

    # シンボルを計算
    A = computesymbols(chebyshev, [1], π * ones(dimension))

    # 検証
    eigenvalues = real(eigvals(A))
    if dimension == 1
        @assert minimum(eigenvalues) ≈ 0.15151515151515105
        @assert maximum(eigenvalues) ≈ 0.27272727272727226
    elseif dimension == 2
        @assert minimum(eigenvalues) ≈ -0.25495098334134725
        @assert maximum(eigenvalues) ≈ -0.17128758445192374
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ -0.8181818181818181
        @assert maximum(eigenvalues) ≈ -0.357575757575757
    end
end

# 出力

```
