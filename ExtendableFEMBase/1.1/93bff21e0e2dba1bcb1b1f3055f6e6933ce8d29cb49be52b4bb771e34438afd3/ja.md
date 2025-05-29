```
function FESpace{FEType<:AbstractFiniteElement,AT<:AssemblyType}(
	xgrid::ExtendableGrid{Tv,Ti};
	name = "",
	broken::Bool = false)
```

指定された FEType の FESpace のコンストラクタで、AT = ON*CELLS/ON*FACES/ON*EDGES は提供された xgrid のセル/フェイス/エッジ上に有限要素空間を生成します（省略された場合はデフォルトで ON*CELLS が使用されます）。broken スイッチを使用すると、破損した有限要素空間（すなわち、区分的 H1/Hdiv/HCurl）を生成できます。名前が提供されていない場合、自動的に FEType から生成されます。AT が提供されていない場合、空間は ON_CELLS で生成されます。
