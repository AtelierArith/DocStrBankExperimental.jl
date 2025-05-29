`HCAT(A::AbstractOperator...)`

ショートハンドコンストラクタ: 

`[A1 A2 ...]` 

`hcat(A...)` 

`AbstractOperator`を水平方向に連結します。すべての演算子は同じコドメインの次元と型を共有する必要があります。例えば、`size(A1,1) == size(A2,1)` および `codomainType(A1) == codomainType(A2)` です。

```julia
julia> HCAT(DFT(10),DCT(Complex{Float64},20)[1:10])
[ℱ,↓*ℱc]  ℝ^10  ℂ^20 -> ℂ^10

julia> H = [Eye(10) DiagOp(2*ones(10))]
[I,╲]  ℝ^10  ℝ^10 -> ℝ^10

julia> hcat(H,DCT(10))
HCAT  ℝ^10  ℝ^10  ℝ^10 -> ℝ^10

```

`HCAT`演算子を評価するには、正しい次元と型の`AbstractArray`の`Tuple`でそれらを掛けます。

```julia
julia> H*ArrayPartition(ones(10),ones(10))
3-element Array{Float64,1}:
 3.0
 3.0
 3.0
 ...
```
