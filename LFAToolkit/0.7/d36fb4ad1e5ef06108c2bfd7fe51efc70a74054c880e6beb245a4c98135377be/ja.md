```julia
computesymbols(operator, θ)
```

演算子のシンボル行列を計算します

# 引数:

  * `operator::Operator`:  シンボル行列を計算する有限要素演算子
  * `θ::Array{Real}`:      フーリエモード周波数配列（次元ごとに1つの周波数）

# 戻り値:

  * 演算子のシンボル行列

# 例:

```jldoctest
using LinearAlgebra;

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

    # シンボルを計算
    A = computesymbols(diffusion, π * ones(dimension))

    # 検証
    eigenvalues = real(eigvals(A))
    if dimension == 1
        @assert minimum(eigenvalues) ≈ 1
        @assert maximum(eigenvalues) ≈ 4 / 3
    elseif dimension == 2
        @assert minimum(eigenvalues) ≈ 2 / 3
        @assert maximum(eigenvalues) ≈ 64 / 45
    elseif dimension == 3
        @assert minimum(eigenvalues) ≈ 1 / 3
        @assert maximum(eigenvalues) ≈ 256 / 225
    end
end

# 出力

```
