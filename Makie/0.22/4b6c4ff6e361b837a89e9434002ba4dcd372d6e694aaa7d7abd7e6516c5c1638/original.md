```
axislegend(ax, args...; position = :rt, kwargs...)
axislegend(ax, args...; position = (1, 1), kwargs...)
axislegend(ax = current_axis(); kwargs...)
axislegend(title::AbstractString; kwargs...)
axislegend(ax, title::AbstractString; kwargs...)
```

Create a legend that sits inside an Axis's plot area.

The position can be a Symbol where the first letter controls the horizontal alignment and can be l, r or c, and the second letter controls the vertical alignment and can be t, b or c. Or it can be a tuple where the first element is set as the Legend's halign and the second element as its valign.

With the keywords merge and unique you can control how plot objects with the same labels are treated. If merge is true, all plot objects with the same label will be layered on top of each other into one legend entry. If unique is true, all plot objects with the same plot type and label will be reduced to one occurrence.
