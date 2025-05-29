```
function nodevalues_subset!(
	target::AbstractArray{<:Real,2},
	source::AbstractArray{T,1},
	FE::FESpace{Tv,Ti,FEType,AT},
	operator::Type{<:AbstractFunctionOperator} = Identity;
	regions::Array{Int,1} = [0],
	abs::Bool = false,
	factor = 1,
	nodes = [],				  
	target_offset::Int = 0,   # start to write into target after offset
	zero_target::Bool = true, # target vector is zeroed
	continuous::Bool = false)
```

有限要素関数を係数ベクトル source（FESpace FE の係数ベクトルとして解釈される）と指定された FunctionOperator を使用して、グリッドの指定されたノードのリストに対して評価し、その値をその順序で target に書き込みます。指定された領域（デフォルト = すべての領域）の一部でないノードの値はゼロに設定されます。非連続（continuous = false）量は、各ノードの指定された領域内のすべての隣接セルで評価され、その後平均化されます。連続（continuous = true）量は、各ノードで一度だけ評価されます。
