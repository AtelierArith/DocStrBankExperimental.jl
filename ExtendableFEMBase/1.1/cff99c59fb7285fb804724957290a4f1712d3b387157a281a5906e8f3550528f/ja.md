```
function lazy_interpolate!(
	target::FEVectorBlock{T1,Tv,Ti},
	source::FEVectorBlock{T2,Tv,Ti};
	operator = Identity,
	postprocess = nothing,
	xtrafo = nothing,
	items = [],
	not_in_domain_value = 1e30,
	eps = 1e-13,
	use_cellparents::Bool = false) where {T1,T2,Tv,Ti}
```

与えられた有限要素関数をターゲットのFEVectorBlockに割り当てられた有限要素空間に補間します。（現在のところ、これはPointEvaluationパターンとセル検索に基づいているため、最も効率的な方法ではありません。ターゲットグリッドのグリッドコンポーネントにCellParentsが利用可能な場合、これらの親セル情報を使用して検索を改善できます。これを有効にするには、'use_cellparents' = trueを設定してください。）与えられたカーネル関数は、インターフェースに準拠しています。

```
kernel!(result, input, qpinfo)
```

オペレーター評価（=入力）は、さらに後処理できます。qpinfo引数を使用すると、現在の数値積分点での情報にアクセスできます。

注意：ターゲットグリッドの頂点での不連続量は、ソースグリッドの最初に見つかったセルで評価されます。平均化は行われません。epsを使用すると、ExtendableGrids.CellFinderを介したセル検索の許容誤差を調整できます。
