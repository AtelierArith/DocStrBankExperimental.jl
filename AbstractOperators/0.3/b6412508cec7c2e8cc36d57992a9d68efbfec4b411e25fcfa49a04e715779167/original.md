`ndoms(L::AbstractOperator, [dom::Int]) -> (number of codomains, number of domains)`

Returns the number of codomains and domains  of a `AbstractOperator`. Optionally you can specify the codomain (with `dom = 1`) or the domain (with `dom = 2`)

```julia
julia > ndoms(DFT(10,10))
(1,1)

julia> ndoms(hcat(DFT(10,10),DFT(10,10)))
(1, 2)

julia> ndoms(hcat(DFT(10,10),DFT(10,10)),2)
2

julia> ndoms(DCAT(DFT(10,10),DFT(10,10)))
(2,2)
```
