`DCAT(A::AbstractOperator...)`

Block-diagonally concatenate `AbstractOperator`s.

```julia
julia> D = DCAT(HCAT(Eye(2),Eye(2)),DFT(3))
[[I,I],0;0,ℱ]  ℝ^2  ℝ^2  ℝ^4 -> ℝ^2  ℂ^3

julia> DCAT(Eye(10),Eye(10),FiniteDiff((4,4)))
DCAT  ℝ^10  ℝ^10  ℝ^(4, 4) -> ℝ^10  ℝ^10  ℝ^(3, 4)
```

To evaluate `DCAT` operators multiply them with a `Tuple` of `AbstractArray` of the correct domain size and type. The output will consist as well of a `Tuple` with the codomain type and size of the `DCAT`.

```julia
julia> D*ArrayPartition(ones(2),ones(2),ones(3))
([2.0, 2.0], Complex{Float64}[3.0+0.0im, 0.0+0.0im, 0.0+0.0im])

```
