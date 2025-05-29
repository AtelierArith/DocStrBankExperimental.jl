```
AbstractZonotope{N} <: AbstractCentrallySymmetricPolytope{N}
```

ゾノトピック集合のための抽象型。

### 注意事項

数学的に、ゾノトープは次の集合として定義されます。

$$
Z = \left\{ c + ∑_{i=1}^p ξ_i g_i,~~ ξ_i ∈ [-1, 1]~~ ∀ i = 1,…, p \right\},
$$

ここで、$c ∈ ℝ^n$ はその中心であり、$\{g_i\}_{i=1}^p$, $g_i ∈ ℝ^n$ は生成子の集合です。この特徴付けは、ゾノトープを線分の有限ミンコフスキー和として定義します。ゾノトープは、$ℝ^n$ における単位無限ノルムボールのアフィン変換による像として同等に記述できます。

このインターフェースの標準実装については [`Zonotope`](@ref) を参照してください。

すべての具体的な `AbstractZonotope` は、以下の関数を定義する必要があります：

  * `generators(::AbstractZonotope)` – 生成子のイテレータを返す
  * `genmat(::AbstractZonotope)` – 生成子行列を返す

関数 `genmat` と `generators` は互いに定義できるため、実際にはどちらか一方を実装すれば十分であり、もう一方の関数の実装はフォールバック実装 `genmat_fallback` または `generators_fallback` を呼び出すことができます。

`AbstractZonotope` のサブタイプ（抽象インターフェースを含む）：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractZonotope)
4-element Vector{Any}:
 AbstractHyperrectangle
 HParallelotope
 LineSegment
 Zonotope
```
