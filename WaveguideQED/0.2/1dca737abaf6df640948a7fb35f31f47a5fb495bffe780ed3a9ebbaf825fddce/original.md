```
plot_twophoton!(ax,twophotonstate::TwophotonView,times;kwargs...)
plot_twophoton!(ax,twophotonstate::TwoWaveguideView,times;kwargs...)
plot_twophoton!(ax,state::Ket,times;kwargs...)
plot_twophoton!(ax,twophotonstate,times;kwargs...)
```

Plots the twophoton state in the given ax. 

# Arguments

  * ax of type PyObject <AxesSubplot: > from `PyPlot`
  * State to be plotted twophotonstate or state. If state is a `Ket` [`TwoPhotonView`](@ref) is called to extract twophotonstate. Otherwise twophotonstate should be AbstractArray of dimensions (length(times),length(times)).

#Return ax.contour object with the plotted state.
