```
function nodevalues(
    source::FEVectorBlock,
    operator::Type{<:AbstractFunctionOperator} = Identity;
    regions::Array{Int,1} = [0],
    abs::Bool = false,
    factor = 1,
    target_offset::Int = 0,   # start to write into target after offset
    zero_target::Bool = true, # target vector is zeroed
    continuous::Bool = false)
```

有限要素関数を係数ベクトル source と指定された FunctionOperator でグリッドのすべてのノード（指定された領域の）で評価し、値を持つ配列を返します。非連続（continuous = false）量は平均化されます。
