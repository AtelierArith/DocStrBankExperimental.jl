Cost interface, implement the following functions

see also `AbstractModel`, `ModelAndCost`

```
function calculate_cost(::Type{AbstractCost}, x::AbstractVector, u)::Number

function calculate_cost(::Type{AbstractCost}, x::AbstractMatrix, u)::AbstractVector

function calculate_final_cost(::Type{AbstractCost}, x::AbstractVector)::Number

function dc(::Type{AbstractCost}, x, u)
    return cx,cu,cxx,cuu,cxu
end
```
