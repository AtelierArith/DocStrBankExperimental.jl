```julia
computesymbolsoverrange(
    operator,
    numbersteps1d;
    mass = nothing,
    θ_min = -π / 2,
    θ_band = 2π,
)
```

演算子のθの範囲に対するシンボル行列の固有値と固有ベクトルを計算します

# 引数:

  * `operator::Operator`:  シンボル行列を計算する有限要素演算子
  * `numbersteps1d::Int`:  各次元でサンプリングするθの値の数; 注意: `numbersteps1d`^`dimension` のシンボル行列が計算されます

# キーワード引数:

  * `mass::Union{Operator,Nothing} = nothing`:  分析解と比較するために反転する質量演算子
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

    # シンボルを計算
    (_, eigenvalues, _) = computesymbolsoverrange(diffusion, numbersteps1d)

    # 検証
    eigenvalues = real(eigenvalues)
    if dimension == 1
        @assert minimum(eigenvalues[4, :]) ≈ 1
        @assert maximum(eigenvalues[4, :]) ≈ 4 / 3
    elseif dimension == 2
        @assert minimum(eigenvalues[19, :]) ≈ 2 / 3
        @assert maximum(eigenvalues[19, :]) ≈ 64 / 45
    elseif dimension == 3
        @assert minimum(eigenvalues[94, :]) ≈ 1 / 3
        @assert maximum(eigenvalues[94, :]) ≈ 256 / 225
    end
end

# 出力

```

```jldoctest
# セットアップ
numbersteps1d = 3;
mesh = Mesh2D(0.5, 0.5);
p = 6;

# 演算子
mass = GalleryOperator("mass", p + 1, p + 1, mesh);
diffusion = GalleryOperator("diffusion", p + 1, p + 1, mesh);

# シンボルを計算
(_, eigenvalues, _) =
    computesymbolsoverrange(diffusion, numbersteps1d; mass = mass, θ_min = -π);
eigenvalues = real(eigenvalues);

@assert minimum(eigenvalues[2, :]) ≈ π^2

# 出力

```
