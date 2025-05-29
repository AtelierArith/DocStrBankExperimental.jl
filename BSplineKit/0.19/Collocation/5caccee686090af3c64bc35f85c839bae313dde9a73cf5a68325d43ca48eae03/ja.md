```
collocation_matrix(
    B::AbstractBSplineBasis,
    x::AbstractVector,
    [deriv::Derivative = Derivative(0)],
    [MatrixType = CollocationMatrix{Float64}];
    clip_threshold = eps(eltype(MatrixType)),
)
```

Bスプライン係数をコレクションポイント `x` でのスプライン値にマッピングするコレクション行列を返します。

# 拡張ヘルプ

行列の要素は、コレクションポイントで評価されたBスプラインによって与えられます：

$$
C_{ij} = b_j(x_i) \quad \text{for} \quad
i ∈ [1, N_x] \text{ and } j ∈ [1, N_b],
$$

ここで `Nx = length(x)` はコレクションポイントの数、`Nb = length(B)` は `B` のBスプラインの数です。

Bスプラインの導関数に関連する行列を取得するには、`deriv` 引数を導関数の次数に設定します。

Bスプライン係数 $\{u_j, 1 ≤ j ≤ N_b\}$ が与えられた場合、コレクションポイントでのスプラインの値（または導関数）を `v = C * u` として復元できます。逆に、コレクションポイントでの値 $v_i$ がわかっている場合、コレクションポイントを通るスプラインの係数 $u$ は線形システム `u = C \ v` の逆行列を用いて取得できます。

`clip_threshold` 引数は、Bスプラインを評価する際に得られるスプリアスで無視できる値を無視することを可能にします。これらの値は通常不要であり、行列の要素数（および時にはバンド幅）を人工的に増加させます。コレクションポイントがノット上にある場合に現れることがあります。デフォルトでは、`clip_threshold` は行列要素タイプに関連するマシンイプシロンに設定されています（Juliaドキュメントの `eps` を参照）。この動作を無効にするには、ゼロに設定します。

## 行列タイプ

`MatrixType` のオプション引数は、返される行列のタイプを選択することを可能にします。

Bスプラインのコンパクトサポートにより、コレクションポイントが適切に分布している場合、コレクション行列は [バンド行列](https://en.wikipedia.org/wiki/Band_matrix) です。

### サポートされている行列タイプ

  * `CollocationMatrix{T}`: `BandedMatrix{T}` に似ており、ピボットなしで効率的なLU因数分解を行います（詳細は [`CollocationMatrix`](@ref) を参照）。このオプションは、線形システムの逆行列に対してスパース行列よりもはるかに優れた性能を発揮します。一方、行列ベクトルまたは行列行列の乗算に関しては、特にOpenBLASを使用する場合、`SparseMatrixCSC` の方がパフォーマンスが良いことがあります（[BandedMatrices issue](https://github.com/JuliaLinearAlgebra/BandedMatrices.jl/issues/110) を参照）。非正方行列の形状やコレクションポイントの分布が適切でない場合、エラーが発生することがあります。この場合、行列の実際のバンド幅は期待されるバンド幅よりも大きくなる可能性があります。
  * `SparseMatrixCSC{T}`: 通常のスパース行列；すべての行列形状を正しく処理します。
  * `Matrix{T}`: 通常の密行列。一般的に、特に大規模な問題に対しては代替案よりもパフォーマンスが劣ります。

!!! note "周期的Bスプライン基底"
    デフォルトの行列タイプは `CollocationMatrix{T}` ですが、周期的基底（[`PeriodicBSplineBasis`](@ref)）の場合は、周期性のためにコレクション行列にいくつかのバンド外のエントリがあります。*三次*周期的基底の場合、[`Collocation.CyclicTridiagonalMatrix`](@ref) 行列タイプが使用され、線形問題の効率的な解法を実装します。非三次周期的基底の場合、デフォルトは `SparseMatrixCSC` です。これは将来的に変更される可能性があることに注意してください。


他にも [`collocation_matrix!`](@ref) を参照してください。
