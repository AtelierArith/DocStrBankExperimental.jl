`HCAT(A::AbstractOperator...)`

Shorthand constructors: 

`[A1 A2 ...]` 

`hcat(A...)` 

Horizontally concatenate `AbstractOperator`s. Notice that all the operators must share the same codomain dimensions and type, e.g. `size(A1,1) == size(A2,1)` and `codomainType(A1) == codomainType(A2)`.

```julia
julia> HCAT(DFT(10),DCT(Complex{Float64},20)[1:10])
[ℱ,↓*ℱc]  ℝ^10  ℂ^20 -> ℂ^10

julia> H = [Eye(10) DiagOp(2*ones(10))]
[I,╲]  ℝ^10  ℝ^10 -> ℝ^10

julia> hcat(H,DCT(10))
HCAT  ℝ^10  ℝ^10  ℝ^10 -> ℝ^10

```

To evaluate `HCAT` operators multiply them with a `Tuple` of `AbstractArray` of the correct dimensions and type. 

```julia
julia> H*ArrayPartition(ones(10),ones(10))
3-element Array{Float64,1}:
 3.0
 3.0
 3.0
 ...
```
