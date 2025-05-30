```
function nodevalues!(
    target::AbstractArray{<:Real,2},
    source::AbstractArray{T,1},
    FE::FESpace{Tv,Ti,FEType,AT},
    operator::Type{<:AbstractFunctionOperator} = Identity;
    regions::Array{Int,1} = [0],
    abs::Bool = false,
    factor = 1,
    target_offset::Int = 0,   # start to write into target after offset
    zero_target::Bool = true, # target vector is zeroed
    continuous::Bool = false)
```

有限要素関数を係数ベクトル source（FESpace FE の係数ベクトルとして解釈される）と指定された FunctionOperator を用いて、グリッドの（指定された領域の）すべてのノードで評価し、値を target に書き込みます。非連続（continuous = false）量は平均化されます。
