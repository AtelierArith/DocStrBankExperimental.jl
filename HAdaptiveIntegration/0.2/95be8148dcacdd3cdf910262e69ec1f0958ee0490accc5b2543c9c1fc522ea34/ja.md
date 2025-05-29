```
integrate(
    fct,
    domain::AbstractDomain{D,T};
    embedded_cubature::EmbeddedCubature{D,T}=default_embedded_cubature(domain),
    subdiv_algo=default_subdivision(domain),
    buffer=nothing,
    norm=x -> LinearAlgebra.norm(x, Inf),
    atol=zero(T),
    rtol=(atol > zero(T)) ? zero(T) : sqrt(eps(T)),
    maxsubdiv=8192 * 2^D,
) where {D,T}
```

関数 `fct` の `domain` 上の積分を `I` とし、誤差推定を `E` とします。

## 引数

  * `fct`: `SVector{D,T}` を受け取り、戻り値の型 `K` を返す関数で、`K` は型 `T` のスカラーとの乗算と加算をサポートする必要があります。
  * `domain::AbstractDomain{D,T}`: 積分領域。現在、[`Triangle`](@ref)、[`Rectangle`](@ref)、[`Tetrahedron`](@ref)、[`Cuboid`](@ref)、`d` 次元の [`Simplex`](@ref)、および `d` 次元の [`Orthotope`](@ref) をサポートしています。

## オプション引数

  * `embedded_cubature::EmbeddedCubature{D,T}=default_embedded_cubature(domain)`: 埋め込みキュバチュア、各サポートされている領域には [`default_embedded_cubature`](@ref) があります。
  * `subdiv_algo=default_subdivision(domain)`: 分割アルゴリズム、各領域には [`default_subdivision`](@ref) があります。
  * `buffer=nothing`: 適応アルゴリズムを行うためのヒープ、[`allocate_buffer`](@ref) を使用して割り当てることができ、複数回の `integrate` 呼び出しでパフォーマンス向上が期待できます。
  * `norm=x -> LinearAlgebra.norm(x, Inf)`: 誤差推定に使用されるノルム。
  * `atol=zero(T)`: 絶対許容誤差。
  * `rtol=(atol > zero(T)) ? zero(T) : sqrt(eps(T))`: 相対許容誤差。
  * `maxsubdiv=8192 * 2^D`: 最大分割数。
