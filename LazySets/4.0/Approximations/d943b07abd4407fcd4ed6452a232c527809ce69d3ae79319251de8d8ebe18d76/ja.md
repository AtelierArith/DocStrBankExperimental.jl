```
overapproximate(vTM::Vector{TaylorModelN{N, T, S}}, ::Type{<:Zonotope};
                [remove_redundant_generators]::Bool=true
                [normalize]::Bool=true) where {N, T, S}
```

多変数テイラーモデルをゾノトープで過大評価します。

### 入力

  * `vTM`       – `TaylorModelN`のベクトル
  * `Zonotope`  – 目標集合の型
  * `remove_redundant_generators` – （オプション; デフォルト: `true`）結果のゾノトープの冗長な生成子を削除するフラグ
  * `normalize` – （オプション; デフォルト: `true`）テイラーモデルの正規化をスキップするフラグ

### 出力

与えられたテイラーモデルの範囲を過大評価するゾノトープ。

### 例

次のように、順序2および4の2次元テイラーモデルのベクトルを考えます。

```jldoctest
julia> using LazySets, TaylorModels

julia> const IA = IntervalArithmetic;

julia> x₁, x₂ = set_variables(Float64, ["x₁", "x₂"], order=8)
2-element Vector{TaylorN{Float64}}:
  1.0 x₁ + 𝒪(‖x‖⁹)
  1.0 x₂ + 𝒪(‖x‖⁹)

julia> x₀ = IA.IntervalBox(0..0, 2) # 拡張点
[0, 0]²

julia> Dx₁ = IA.interval(0.0, 3.0) # x₁のドメイン
[0, 3]

julia> Dx₂ = IA.interval(-1.0, 1.0) # x₂のドメイン
[-1, 1]

julia> D = Dx₁ × Dx₂ # 各変数のドメインの直積を取る
[0, 3] × [-1, 1]

julia> r = IA.interval(-0.5, 0.5) # 区間余剰
[-0.5, 0.5]

julia> p1 = 1 + x₁^2 - x₂
 1.0 - 1.0 x₂ + 1.0 x₁² + 𝒪(‖x‖⁹)

julia> p2 = x₂^3 + 3x₁^4 + x₁ + 1
 1.0 + 1.0 x₁ + 1.0 x₂³ + 3.0 x₁⁴ + 𝒪(‖x‖⁹)

julia> vTM = [TaylorModelN(pi, r, x₀, D) for pi in [p1, p2]]
2-element Vector{TaylorModelN{2, Float64, Float64}}:
            1.0 - 1.0 x₂ + 1.0 x₁² + [-0.5, 0.5]
  1.0 + 1.0 x₁ + 1.0 x₂³ + 3.0 x₁⁴ + [-0.5, 0.5]

julia> Z = overapproximate(vTM, Zonotope);

julia> center(Z)
2-element Vector{Float64}:
   5.5
 124.0

julia> Matrix(genmat(Z))
2×2 Matrix{Float64}:
   0.0  -6.0
 124.5   0.0
```

### アルゴリズム

単変数の場合のアルゴリズムの説明を参照してください。
