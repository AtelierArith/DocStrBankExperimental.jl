```
TotalMassFlux(scale = si_unit(:day), max_abs = nothing, max_rel = nothing)
```

Variable normally used as primary variable. Represents the total mass flux going through a face. The typical usage is the mass flow through a segment of a [`MultiSegmentWell`](@ref).

Note that the flow direction can often switch signs over a segment during a complex simulation. Setting `max_rel` to something other than `nothing` can therefore lead to severe convergence issues in the case of flow reversal.

# Fields (as keyword arguments)

  * `scale`: Scaling for variable
  * `max_abs`: Max absolute change between Newton iterations
  * `max_rel`: Maximum relative change between Newton iterations
