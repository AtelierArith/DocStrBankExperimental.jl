```
function nodevalues!(
    target::AbstractArray{<:Real,2},
    source::FEVectorBlock,
    operator::Type{<:AbstractFunctionOperator} = Identity;
    regions::Array{Int,1} = [0],
    abs::Bool = false,
    factor = 1,
    target_offset::Int = 0,   # start to write into target after offset
    zero_target::Bool = true, # target vector is zeroed
    continuous::Bool = false)
```

指定された領域のグリッドのすべてのノードで、係数ベクトルsourceと指定されたFunctionOperatorを使用して有限要素関数を評価し、その値をtargetに書き込みます。非連続（continuous = false）量は平均化されます。
