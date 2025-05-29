`VCAT(A::AbstractOperator...)`

Shorthand constructors: 

`[A1; A2 ...]` 

`vcat(A...)` 

Vertically concatenate `AbstractOperator`s. Notice that all the operators must share the same domain dimensions and type, e.g. `size(A1,2) == size(A2,2)` and `domainType(A1) == domainType(A2)`.

```julia
julia> VCAT(DFT(4,4),Variation((4,4)))
[ℱ;Ʋ]  ℝ^(4, 4) -> ℂ^(4, 4)  ℝ^(16, 2)

julia> V = [Eye(3); DiagOp(2*ones(3))]
[I;╲]  ℝ^3 -> ℝ^3  ℝ^3

julia> vcat(V,FiniteDiff((3,)))
VCAT  ℝ^3 -> ℝ^3  ℝ^3  ℝ^2
```

When multiplying a `VCAT` with an array of the proper size, the result will be a `Tuple` containing arrays with the `VCAT`'s codomain type and size.

```julia
julia> V*ones(3)
([1.0, 1.0, 1.0], [2.0, 2.0, 2.0])

```
