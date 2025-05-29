```
title(ctx::Context, str::String, props::Property...) -> Context
```

Add a title string to a group of plots, typically created with [`vstack`](@ref), [`hstack`](@ref), or [`gridstack`](@ref).

# Examples

```
p1 = plot(x=[1,2], y=[3,4], Geom.line);
p2 = plot(x=[1,2], y=[4,3], Geom.line);
title(hstack(p1,p2), "my latest data", Compose.fontsize(18pt), fill(colorant"red"))
```
