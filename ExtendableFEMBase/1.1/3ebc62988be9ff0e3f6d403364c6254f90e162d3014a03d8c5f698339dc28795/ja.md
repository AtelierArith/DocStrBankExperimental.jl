```
function unicode_gridplot(
	xgrid::ExtendableGrid;
	title = "gridplot",
	resolution = (40,20),
	color = (200,200,200),
	bface_color = (255,0,0),
	CanvasType = BrailleCanvas,
	plot_based = ON_CELLS,   # or ON_FACES/ON_EDGES
	kwargs...
```

(UnicodePlotsを必要とする拡張を介して)

三角形分割のすべてのエッジを描画することによって、UnicodePlotsキャンバス（デフォルト：BrailleCanvas）上にグリッドをプロットします。
