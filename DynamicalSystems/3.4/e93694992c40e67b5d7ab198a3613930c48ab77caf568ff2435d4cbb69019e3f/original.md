```
interactive_poincaresos_scan(A::StateSpaceSet, j::Int; kwargs...)
interactive_poincaresos_scan(As::Vector{StateSpaceSet}, j::Int; kwargs...)
```

Launch an interactive application for scanning a Poincare surface of section of `A` like a "brain scan", where the plane that defines the section can be arbitrarily moved around via a slider. Return `figure, ax3D, ax2D`.

The input dataset must be 3 dimensional, and here the crossing plane is always chosen to be when the `j`-th variable of the dataset crosses a predefined value. The slider automatically gets all possible values the `j`-th variable can obtain.

If given multiple datasets, the keyword `colors` attributes a color to each one, e.g. `colors = [JULIADYNAMICS_COLORS[mod1(i, 6)] for i in 1:length(As)]`.

The keywords `linekw, scatterkw` are named tuples that are propagated as keyword arguments to the line and scatter plot respectively, while the keyword `direction = -1` is propagated to the function `DyamicalSystems.poincaresos`.
