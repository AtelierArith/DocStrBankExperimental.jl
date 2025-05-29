```julia
computesymbols(bddc, ω, θ)
```

BDDC前処理オペレーターのシンボル行列を計算します

# 引数:

  * `bddc::BDDC`:      シンボル行列を計算するためのBDDC前処理器
  * `ω::Array{Real}`:  BDDCスムージングパラメータ
  * `θ::Array{Real}`:  フーリエモード周波数配列（次元ごとに1つの周波数）

# 戻り値:

  * BDDC前処理オペレーターのシンボル行列

# 集約BDDCの例:

```jldoctest
using LinearAlgebra;

for dimension = 2:3
    # セットアップ
    mesh = []
    if dimension == 2
        mesh = Mesh2D(1.0, 1.0)
    elseif dimension == 3
        mesh = Mesh3D(1.0, 1.0, 1.0)
    end
    diffusion = GalleryOperator("diffusion", 3, 3, mesh)
    bddc = LumpedBDDC(diffusion)

    # シンボルを計算
    A = computesymbols(bddc, [0.2], π * ones(dimension))

    # 検証
    eigenvalues = real(eigvals(A))
    if dimension == 2
        @assert minimum(eigenvalues) ≈ 0.43999999999999995
        @assert maximum(eigenvalues) ≈ 0.8
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ -0.6319999999999972
        @assert maximum(eigenvalues) ≈ 0.8
    end
end

# 出力

```

# ディリクレBDDCの例:

```jldoctest
using LinearAlgebra;

for dimension = 2:3
    # セットアップ
    mesh = []
    if dimension == 2
        mesh = Mesh2D(1.0, 1.0)
    elseif dimension == 3
        mesh = Mesh3D(1.0, 1.0, 1.0)
    end
    diffusion = GalleryOperator("diffusion", 3, 3, mesh)
    bddc = DirichletBDDC(diffusion)

    # シンボルを計算
    A = computesymbols(bddc, [0.2], π * ones(dimension))

    # 検証
    eigenvalues = real(eigvals(A))
    if dimension == 2
        @assert minimum(eigenvalues) ≈ 0.7999999999999998
        @assert maximum(eigenvalues) ≈ 0.8
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ 0.7801226993865031
        @assert maximum(eigenvalues) ≈ 0.8
    end
end

# 出力

```
