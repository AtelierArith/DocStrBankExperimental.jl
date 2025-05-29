```julia
Plot_History(sc::SelfCons{T, R, S}, arg::String ; indices::Vector{Int64} = collect(1:length(sc.Initial)), plot_legend::Bool = true) where {T<:Function, R<:Function, S<:Union{Number, Vector{<:Number}}}
```

Plotting function to plot the flow of `sc.VIns`, `sc.VOuts`, or the convergence as a function of iteration, when `arg` = "inputs", "outputs", or "convergence" respectively. Optional argument `indices` is if you only want to plot a subset of the vector arguments. `log_plot` is if you want to plot the semi-log plot of convergence vs iteration
