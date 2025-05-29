```
modelBackground(spec::Spectrum, chs::AbstractUnitRange{<:Integer}, ash::AtomicSubShell)
```

spec: A spectrum containing a peak centered on chs chs:  A range of channels containing a peak ash:  The edge (as an AtomicSubShell)

A simple model for modeling the background under a characteristic x-ray peak. The model fits a line to low and high energy background regions around firsr(chs) and last(chs). If the low energy line extended out to the edge energy is larger than the high energy line at the same energy, then a negative going edge is fit between the two. Otherwise a line is fit between the low energy side and the high energy side. This model only works when there are no peak interference over the range chs.

```
modelBackground(spec::Spectrum, chs::AbstractUnitRange{<:Integer})
modelBackground(spec::Spectrum, chs::AbstractUnitRange{<:Integer}, ash::AtomicSubShell)
```

`spec`: A spectrum containing a peak centered on chs `chs`:  A range of channels containing a peak `ash`:  The largest edge within the range of channels `chs` associated with the characteristic peak

A simple model for modeling the background under a characteristic x-ray peak. The model fits a line between the  low and high energy background regions around first(chs) and last(chs). This model only works when there are no peak interference over the range chs.
