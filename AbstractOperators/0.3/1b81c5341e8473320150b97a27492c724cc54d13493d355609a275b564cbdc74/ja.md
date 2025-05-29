`VCAT(A::AbstractOperator...)`

ショートハンドコンストラクタ:

`[A1; A2 ...]`

`vcat(A...)`

`AbstractOperator`を垂直に連結します。すべての演算子は同じドメインの次元とタイプを共有する必要があります。例えば、`size(A1,2) == size(A2,2)` および `domainType(A1) == domainType(A2)`。

```julia
julia> VCAT(DFT(4,4),Variation((4,4)))
[ℱ;Ʋ]  ℝ^(4, 4) -> ℂ^(4, 4)  ℝ^(16, 2)

julia> V = [Eye(3); DiagOp(2*ones(3))]
[I;╲]  ℝ^3 -> ℝ^3  ℝ^3

julia> vcat(V,FiniteDiff((3,)))
VCAT  ℝ^3 -> ℝ^3  ℝ^3  ℝ^2
```

適切なサイズの配列と `VCAT` を掛けると、結果は `VCAT` のコドメインタイプとサイズを持つ配列を含む `Tuple` になります。

```julia
julia> V*ones(3)
([1.0, 1.0, 1.0], [2.0, 2.0, 2.0])

```
