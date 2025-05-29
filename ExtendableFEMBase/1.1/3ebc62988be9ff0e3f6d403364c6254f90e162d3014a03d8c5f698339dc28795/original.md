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

(via extension that requires UnicodePlots)

Plots the grid on a UnicodePlots canvas (default: BrailleCanvas) by drawing all edges in the triangulation.
