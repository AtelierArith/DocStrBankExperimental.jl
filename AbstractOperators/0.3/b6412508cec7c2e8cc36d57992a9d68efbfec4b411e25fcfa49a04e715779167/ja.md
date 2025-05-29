`ndoms(L::AbstractOperator, [dom::Int]) -> (コドメインの数, ドメインの数)`

`AbstractOperator`のコドメインとドメインの数を返します。オプションでコドメイン（`dom = 1`）またはドメイン（`dom = 2`）を指定できます。

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
