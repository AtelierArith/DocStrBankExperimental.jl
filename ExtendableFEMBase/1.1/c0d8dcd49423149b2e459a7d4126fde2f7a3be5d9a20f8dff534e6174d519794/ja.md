```
function nodevalues(
	source::FEVectorBlock,
	operator::Type{<:AbstractFunctionOperator} = Identity;
	regions::Array{Int,1} = [0],
	abs::Bool = false,
	factor = 1,
	nodes = [],				  
	cellwise = false,		  # セル単位のノード値を返す ncells x nnodes_on_cell (nodes == [] の場合のみ)
	target_offset::Int = 0,   # オフセットの後にターゲットに書き込みを開始
	zero_target::Bool = true, # ターゲットベクトルはゼロに設定される
	continuous::Bool = false)
```

有限要素関数を係数ベクトル source と指定された FunctionOperator を使用して、グリッドの指定されたノードのリスト（デフォルト = すべてのノード）で評価し、その順序でターゲットに値を書き込みます。指定された領域の一部でないノード（デフォルト = すべての領域）はゼロに設定されます。非連続（continuous = false）量は各ノードのすべての隣接セルで評価され、その後平均化されます。連続（continuous = true）量は各ノードで一度だけ評価されます。
