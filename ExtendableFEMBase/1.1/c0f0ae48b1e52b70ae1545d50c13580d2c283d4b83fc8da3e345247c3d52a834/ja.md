```
function nodevalues!(
	target::AbstractArray{<:Real,2},
	source::FEVectorBlock,
	operator::Type{<:AbstractFunctionOperator} = Identity;
	regions::Array{Int,1} = [0],
	abs::Bool = false,
	factor = 1,
	cellwise = false,		  # セルごとのノード値を返す ncells x nnodes_on_cell
	target_offset::Int = 0,   # オフセットの後にターゲットに書き込みを開始
	zero_target::Bool = true, # ターゲットベクトルはゼロに設定される
	continuous::Bool = false)
```

有限要素関数を係数ベクトル source と指定された FunctionOperator で評価し、グリッドの（指定された領域の）すべてのノードに値を書き込みます。非連続（continuous = false）量は各ノードのすべての隣接セルで評価され、その後平均されます。連続（continuous = true）量は各ノードで一度だけ評価されます。
