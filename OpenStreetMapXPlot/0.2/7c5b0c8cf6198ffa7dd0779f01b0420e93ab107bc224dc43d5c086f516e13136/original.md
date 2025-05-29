```
plotmap(nodes::Dict{Int,T},
             bounds::Union{Nothing,OpenStreetMapX.Bounds{T}} = nothing;
             buildings::Union{Nothing,Vector{OpenStreetMapX.Way}} = nothing,
             buildingStyle::Styles=OpenStreetMapXPlot.Style("0x000000", 1, "-"),
             roadways::Union{Nothing,Vector{OpenStreetMapX.Way}} = nothing,
             roadwayStyle::Styles=OpenStreetMapXPlot.Style("0x007CFF", 1.5, "-"),
             walkways::Union{Nothing,Vector{OpenStreetMapX.Way}} = nothing,
             walkwayStyle::Styles=OpenStreetMapXPlot.Style("0x007CFF", 1.5, "-"),
             cycleways::Union{Nothing,Vector{OpenStreetMapX.Way}} = nothing,
             cyclewayStyle::Styles=OpenStreetMapXPlot.Style("0x007CFF", 1.5, "-"),
             features::Union{Nothing,Dict{Int64,Tuple{String,String}}} = nothing,
             featureStyle::Styles=OpenStreetMapXPlot.Style("0xCC0000", 2.5, "."),
             width::Integer=600,
             height::Integer=600,
             fontsize::Integer=0,
             km::Bool=false,
			 use_plain_pyplot::Bool=false
			 ) where T<:Union{OpenStreetMapX.LLA,OpenStreetMapX.ENU}
```

Plots selected map features for a given dictionary of node locations (`nodes`) and within the given `bounds`. The `km` parameter can be used to have a kilometer scale of the map instead of meters.

The default plotting backend is whatever is defined in `Plots.jl`, however if the `use_plain_pyplot` is set to `true` Plots.pythonplot() will be called to switch to PythonPlot backend (note this option is depraciated and normally backend should be changed outside of this function).

Returns an object that can be used for further plot updates.
