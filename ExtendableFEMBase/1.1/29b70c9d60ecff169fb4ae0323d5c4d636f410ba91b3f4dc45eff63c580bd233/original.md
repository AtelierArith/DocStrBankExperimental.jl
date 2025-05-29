```
function unicode_scalarplot(
	u::FEVectorBlock; 
	components = 1:get_ncomponents(u),
	abs = false,
	resolution = (30,30),
	colormap = :viridis,
	title = u.name,
	kwargs...)
```

(via extension that requires UnicodePlots)

Plots components of the finite element function in the FEVectorBlock u by using a lazy_interpolate! onto a coarse uniform mesh and UnicodePlots.jl lineplot or heatmap for 1D or 2D, respectively.

In 1D all components all plotted in the same lineplot, while in 2D all components are plotted in a separate heatmap.

If abs = true, only the absolute value over the components is plotted.
