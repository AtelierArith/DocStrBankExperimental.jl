```
galerkin_matrix(
    [f::Function],
    B::AbstractBSplineBasis,
    [derivatives = (Derivative(0), Derivative(0))],
    [MatrixType = BandedMatrix{Float64}];
    [quadrature = default_quadrature((B, B))],
)
```

ガレルキン質量行列または剛性行列を計算し、これらのより一般的なバリエーションも計算します。

# 拡張ヘルプ

ガレルキン質量行列は次のように定義されます。

$$
M_{ij} = ⟨ ϕ_i, ϕ_j ⟩ \quad \text{for} \quad
i ∈ [1, N] \text{ and } j ∈ [1, N],
$$

ここで、$ϕ_i(x)$は$i$番目の基底関数であり、`N = length(B)`は基底`B`の関数の数です。ここで、$⟨f, g⟩$は関数$f$と$g$の[$L^2$内積](https://en.wikipedia.org/wiki/Square-integrable_function#Properties)です。

Bスプラインの積はそれ自体が区分的多項式であるため、積分は[ガウス求積法則](https://en.wikipedia.org/wiki/Gaussian_quadrature)を使用して正確に計算できます。これを行うために、[FastGaussQuadrature](https://github.com/JuliaApproximation/FastGaussQuadrature.jl)パッケージを介してガウス・レジェンドル求積法を使用します。

## 行列のレイアウトとタイプ

質量行列は$2k - 1$バンドの帯域を持っています。さらに、行列は対称で正定値であり、行列を完全に記述するためには$k$バンドのみが必要です。したがって、基になる行列の[`Hermitian`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/index.html#LinearAlgebra.Hermitian)ビューが返されます。

デフォルトでは、データを保持する基になる行列は対称行列の上部を定義する`BandedMatrix`です。他のタイプのコンテナもサポートされており、通常の疎行列（`SparseMatrixCSC`）や密行列（`Matrix`）が含まれます。行列タイプに関する議論については[`collocation_matrix`](@ref)を参照してください。

!!! note "周期的Bスプライン基底"
    デフォルトの行列タイプは`BandedMatrix`ですが、周期的基底（[`PeriodicBSplineBasis`](@ref)）の場合、ガレルキン行列には周期性のためにいくつかのバンド外のエントリがあります。周期的基底の場合、デフォルトは`SparseMatrixCSC`です。これは将来的に変更される可能性があることに注意してください。


## 基底関数の導関数

基底関数の導関数に関連するガレルキン行列は、オプションの`derivatives`パラメータを使用して構築できます。たとえば、`derivatives = (Derivative(0), Derivative(2))`の場合、行列$⟨ ϕ_i, ϕ_j'' ⟩$が構築され、プライムは導関数を示します。導関数の次数が異なる場合、結果の行列は対称ではなく、その場合は`Hermitian`ビューは返されません。

## 異なる基底の組み合わせ

より一般的には、$⟨ ψ_i^{(n)}, ϕ_j^{(m)} ⟩$の形の行列を計算することが可能であり、ここで`n`と`m`は導関数の次数であり、$ψ_i$と$ϕ_j$は2つの*異なる*（しかし関連する）基底`B₁`と`B₂`に属します。これを行うには、`B`パラメータの代わりに基底のタプル`(B₁, B₂)`を渡す必要があります。制約は、基底が同じ親Bスプライン基底を持っている必要があることです。つまり、同じBスプラインノットのセットを共有し、同じ多項式次数である必要があります。

両方の基底が異なる場合、行列は対称ではなく、基底の長さが異なる場合は正方形にもなりません。

実際には、この機能を使用してBスプライン基底`B`と、`B`から生成された再結合基底`R`を組み合わせることができます（[基底の再結合](@ref basis-recombination-api）を参照）。

## より一般的な関数の統合

より一般的な項を統合したいとします。

$$
L_{ij} = ⟨ f(x) ϕ_i(x), ϕ_j(x) ⟩ = ∫_{a}^{b} f(x) ϕ_i(x) ϕ_j(x) \, \mathrm{d}x
$$

この行列の近似を得るには、$f(x)$関数を最初の位置引数として`galerkin_matrix`（または[`galerkin_matrix!`](@ref)）に渡します。これは、$ϕ_i$または$ϕ_j$の導関数を考慮したい場合は`derivatives`引数と組み合わせることもできます。

この場合、積分の計算が正確であることは保証されていないことに注意してください。なぜなら、ガウス・レジェンドル求積法は被積分関数が多項式であるときのみ「正確」であるからです（2つのBスプラインの積は区分的多項式です）。精度を向上させるために、求積ノードの数$n$を増やすことを検討するかもしれません。そのためには、キーワード引数として`quadrature = Galerkin.gausslegendre(Val(n))`を渡します。 ```
