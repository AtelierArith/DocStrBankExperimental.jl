```julia
computesymbols(multigrid, p, v, θ)
```

ジャコビ前処理演算子のシンボル行列を計算または取得します

# 引数:

  * `multigrid::Multigrid`:  シンボル行列を計算するためのマルチグリッド前処理器
  * `p::Array{Real}`:        スムージングパラメータ配列
  * `v::Array{Int}`:         前後スムージングの反復回数配列、0は前後スムージングなしを示します
  * `θ::Array{Real}`:        フーリエモード周波数配列（次元ごとに1つの周波数）

# 戻り値:

  * マルチグリッド前処理演算子のシンボル行列

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
    ctofbasis = TensorH1LagrangeBasis(3, 5, 1, dimension; collocatedquadrature = true)

    # 演算子
    finediffusion = GalleryOperator("diffusion", 5, 5, mesh)
    coarsediffusion = GalleryOperator("diffusion", 3, 5, mesh)

    # スムーザー
    jacobi = Jacobi(finediffusion)

    # 前処理器
    multigrid = PMultigrid(finediffusion, coarsediffusion, jacobi, [ctofbasis])

    # シンボルを計算
    A = computesymbols(multigrid, [1.0], [1, 1], π * ones(dimension))

    # 検証
    eigenvalues = real(eigvals(A))
    if dimension == 1
        @assert maximum(eigenvalues) ≈ 0.64
    elseif dimension == 2
        @assert maximum(eigenvalues) ≈ 0.9082562365654528
    elseif dimension == 3
        @assert maximum(eigenvalues) ≈ 1.4359882222222669
    end
end

# 出力

```
