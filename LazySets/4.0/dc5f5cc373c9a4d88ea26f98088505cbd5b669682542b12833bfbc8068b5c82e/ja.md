```
AbstractCentrallySymmetricPolytope{N} <: AbstractPolytope{N}
```

中心対称ポリトープ集合のための抽象型です。これは `AbstractCentrallySymmetric` と `AbstractPolytope` インターフェースを組み合わせたものです。このような型の組み合わせは、Juliaが[多重継承](https://github.com/JuliaLang/julia/issues/5)をサポートしない限り必要です。

### 注意事項

すべての具体的な `AbstractCentrallySymmetricPolytope` は、`AbstractPolytope` メソッドに加えて、次の `AbstractCentrallySymmetric` メソッドを定義しなければなりません：

  * `center(::AbstractCentrallySymmetricPolytope)` – 中心点を返す

`AbstractCentrallySymmetricPolytope` のサブタイプ（抽象インターフェースを含む）：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractCentrallySymmetricPolytope)
2-element Vector{Any}:
 AbstractZonotope
 Ball1
```
