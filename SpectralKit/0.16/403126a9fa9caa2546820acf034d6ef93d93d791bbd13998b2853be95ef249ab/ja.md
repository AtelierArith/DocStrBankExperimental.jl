```julia
smolyak_basis(
    univariate_family,
    grid_kind,
    smolyak_parameters,
    _
)

```

スパース Smolyak 基底を作成します。

# 引数

  * `univariate_family`: `grid_kind` と `dimension` パラメータを受け取る呼び出し可能なものである必要があります。例: `Chebyshev`。
  * `grid_kind`: グリッドの種類。例: `InteriorGrid()` など。
  * `smolyak_parameters`: Smolyak グリッド仕様パラメータ。[`SmolyakParameters`](@ref) を参照してください。
  * `N`: 次元。型の安定性のために `Val` でラップされ、整数を受け取る便利なコンストラクタもあります。

## 例

```jldoctest
julia> basis = smolyak_basis(Chebyshev, InteriorGrid(), SmolyakParameters(3), 2)
Sparse multivariate basis on ℝ²
  Smolyak indexing, ∑bᵢ ≤ 3, all bᵢ ≤ 3, dimension 81
  using Chebyshev polynomials (1st kind), InteriorGrid(), dimension: 27

julia> dimension(basis)
81

julia> domain(basis)
[-1,1]²
```

## 特性

*グリッドのネスト*: `SmolyakParameters` の引数を増やすと、粗いグリッドの点を含む洗練されたグリッドが得られます。
