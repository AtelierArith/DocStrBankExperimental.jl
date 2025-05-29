```julia
computesymbolsoverrange(
    multigrid,
    p,
    v,
    numbersteps1d;
    mass = nothing,
    θ_min = -π / 2,
    θ_band = 2π,
)
```

θの範囲にわたる多重格子前処理オペレーターのシンボル行列の固有値と固有ベクトルを計算します。

# 引数:

  * `multigrid::Multigrid`:  シンボル行列を計算するための前処理器
  * `p::Array{Real}`:        スムージングパラメータ配列
  * `v::Array{Int}`:         前後スムージングの反復回数配列、0は前後スムージングなしを示す
  * `numbersteps1d::Int`:    各次元でサンプリングするθの値の数; 注意: `numbersteps1d`^`dimension`のシンボル行列が計算されます

# キーワード引数:

  * `mass::Union{Operator,Nothing} = nothing`:  分析解と比較するために反転する質量オペレーター
  * `θ_min::Real = -π / 2`:                     θの範囲の下限、範囲を`[θ_min, θ_min + θ_band]`にシフトします
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
    ctofbasis = TensorH1LagrangeBasis(3, 5, 1, dimension; collocatedquadrature = true)

    # オペレーター
    finediffusion = GalleryOperator("diffusion", 5, 5, mesh)
    coarsediffusion = GalleryOperator("diffusion", 3, 5, mesh)

    # スムーザー
    jacobi = Jacobi(finediffusion)

    # 前処理器
    multigrid = PMultigrid(finediffusion, coarsediffusion, jacobi, [ctofbasis])

    # シンボルを計算
    (_, eigenvalues, _) = computesymbolsoverrange(multigrid, [1.0], [1, 1], numbersteps1d)

    # 検証
    eigenvalues = real(eigenvalues)
    if dimension == 1
        @assert maximum(eigenvalues[4, :]) ≈ 0.64
    elseif dimension == 2
        @assert maximum(eigenvalues[19, :]) ≈ 0.9082562365654528
    elseif dimension == 3
        @assert maximum(eigenvalues[94, :]) ≈ 1.4359882222222669
    end
end

# 出力

```
