```
QuadratureRule{shape}([::Type{T},] [quad_rule_type::Symbol,] order::Int)
QuadratureRule{shape}(weights::AbstractVector{T}, points::AbstractVector{Vec{rdim, T}})
```

`shape`（[`AbstractRefShape`](@ref)型）の上での積分に使用される`QuadratureRule`を作成します。`order`は数値積分則の次数です。`quad_rule_type`は数値積分則のタイプを決定するオプションの引数で、現在はハイパーキューブ用に`:legendre`と`:lobatto`の規則が実装されています。三角形の場合、次数8までのデフォルトの規則は`:dunavant`によるものです（[Dun:1985:hde](@cite)を参照）。四面体の場合、デフォルトの規則は`keast_minimal`です（[Keast:1986:mtq](@cite)を参照）。ウェッジとピラミッドはデフォルトで`:polyquad`です（[WitVin:2015:isq](@cite)を参照）。さらに、以下が実装されています。

  * 三角形用の`:gaussjacobi`（次数9-15）
  * 四面体用の`:keast_minimal`（[Keast:1986:mtq](@cite)を参照、次数1-5）、負の重みを含む
  * 四面体用の`:keast_positive`（[Keast:1986:mtq](@cite)を参照、次数1-5）、正の重みのみを含む

`QuadratureRule`は、特定の点での関数値の重み付き和によって領域上の積分を近似するために使用されます：

$$
\int\limits_\Omega f(\mathbf{x}) \text{d} \Omega \approx \sum\limits_{q = 1}^{n_q} f(\mathbf{x}_q) w_q
$$

数値積分則は、空間内の$n_q$点$\mathbf{x}_q$と対応する重み$w_q$から構成されます。

Ferriteでは、`QuadratureRule`型は主に[`CellValues`](@ref)を作成するためのコンポーネントの1つとして使用されます。

**一般的なメソッド：**

  * [`getpoints`](@ref) : 数値積分則の点
  * [`getweights`](@ref) : 数値積分則の重み

**例：**

```jldoctest
julia> qr = QuadratureRule{RefTriangle}(1)
QuadratureRule{RefTriangle, Float64, 2}([0.5], Vec{2, Float64}[[0.33333333333333, 0.33333333333333]])

julia> getpoints(qr)
1-element Vector{Vec{2, Float64}}:
 [0.33333333333333, 0.33333333333333]
```
