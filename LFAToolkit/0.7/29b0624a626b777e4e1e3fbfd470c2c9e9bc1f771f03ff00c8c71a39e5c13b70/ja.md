```julia
computesymbolsoverrange(
    preconditioner,
    ω,
    numbersteps1d;
    mass = nothing,
    θ_min = -π / 2,
    θ_band = 2π,
)
```

θの範囲にわたる前処理された演算子のシンボル行列の固有値と固有ベクトルを計算します

# 引数:

  * `preconditioner::AbstractPreconditioner`:  シンボル行列を計算するための前処理器
  * `ω::Array`:                                スムージングパラメータ配列
  * `numbersteps1d::Int`:                      各次元でサンプリングするθの値の数; 注意: `numbersteps1d`^`dimension` のシンボル行列が計算されます

# キーワード引数:

  * `mass::Union{Operator,Nothing} = nothing`:  分析解と比較するために反転させる質量演算子
  * `θ_min::Real = -π / 2`:                     θの範囲の下限、範囲を `[θ_min, θ_min + θ_band]` にシフトします
  * `θ_band::Real = 2π`:                        `θ_max = θ_min + θ_band`

# 戻り値:

タプルを保持します

  * サンプリングされたθの値
  * サンプリングされたθでのシンボル行列の固有値
  * サンプリングされたθでのシンボル行列の固有ベクトル

# 例:

```jldoctest
numbersteps1d = 5;

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
    (_, eigenvalues, _) = computesymbolsoverrange(chebyshev, [1], numbersteps1d)

    # 検証
    eigenvalues = real(eigenvalues)
    if dimension == 1
        @assert minimum(eigenvalues[4, :]) ≈ 0.15151515151515105
        @assert maximum(eigenvalues[4, :]) ≈ 0.27272727272727226
    elseif dimension == 2
        @assert minimum(eigenvalues[19, :]) ≈ -0.25495098334134725
        @assert maximum(eigenvalues[19, :]) ≈ -0.17128758445192374
    elseif dimension == 3
        @assert minimum(eigenvalues[94, :]) ≈ -0.8181818181818181
        @assert maximum(eigenvalues[94, :]) ≈ -0.357575757575757
    end
end

# 出力

```
